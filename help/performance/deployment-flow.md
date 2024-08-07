---
title: 部署流程
description: 瞭解在生產環境中部署Adobe Commerce所需的步驟。
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 部署流程

[!DNL Commerce]生產部署流程可協助存放區達到最大效能。

## 安裝相依性

`composer.json`和`composer.lock`檔案管理[!DNL Commerce]相依性，並為每個套件安裝適當的版本。 如果您打算更新[自動載入器](#update-the-autoloader)，則必須在[前置處理相依性插入指示](#preprocess-dependency-injection-instructions)之前安裝相依性。

若要安裝[!DNL Commerce]相依性：

```bash
composer install --no-dev
```

## 預先處理相依性插入指示

當您預先處理和編譯相依性插入(DI)指示時，請Magento：

* 讀取及處理所有現有的組態
* 分析類別之間的相依性
* 建立自動產生的檔案（包括代理、工廠等）
* 將編譯後的資料和設定儲存在快取中，最多可節省25%的處理請求時間

若要預先處理和編譯DI指示，請執行下列動作：

```bash
bin/magento setup:di:compile
```

## 更新自動載入器

編譯完成後，請確認[APCu已啟用](../performance/software.md#php-settings)並更新自動載入器：

更新自動載入器：

>[!INFO]
>
>`-o`選項會將PSR-0/4自動載入轉換成classmap，以獲得更快的自動載入器。 `--apcu`選項使用APCu來快取found/not-found類別。

```bash
composer dump-autoload -o --apcu
```

如果您計畫更新自動載入器，則必須依序執行下列命令：

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## 部署靜態內容

部署靜態內容導致[!DNL Commerce]執行下列動作：

* 分析所有靜態資源
* 執行內容合併、最小化和整合
* 讀取及處理主題資料
* 分析主題遞補
* 將所有已處理和具體化的內容儲存到特定資料夾，以供日後使用

如果未部署您的靜態內容，[!DNL Commerce]會即時執行所有列出的作業，導致回應時間大幅增加。

您可以使用各種選項，根據存放區大小和履行需求來自訂部署作業。 最常見的是精簡部署策略。 請參閱[靜態檔案部署策略](../configuration/cli/static-view-file-strategy.md)

若要部署靜態內容：

```bash
bin/magento setup:static-content:deploy
```

此命令可讓Composer重新建立專案檔案的對應，以便它們能更快載入。

## 設定生產模式

>[!INFO]
>
>將模式設定為生產模式會自動執行`setup:di:compile`和`setup:static-content:deploy`。

最後，您需要將商店置於生產模式。 生產模式經過專門最佳化，以發揮商店的最大效能。 這也會停用所有開發人員專屬功能。 這可以在您的`.htaccess`或`nginx.conf`檔案中完成：

`SetEnv MAGE_MODE production`

您也可以部署靜態內容、編譯內容，以及在一個CLI命令中設定模式：

```bash
bin/magento deploy:mode:set production
```

命令會在背景執行，不允許您在每個特定步驟上設定其他選項。

## 其他啟動前動作

建議執行這些步驟，但並非強制性。 您可以在以生產模式啟動存放區之前立即執行這些動作。 此清單包括：

* 重新索引資料以避免在索引中出現任何不一致的資料。
* 排清快取以確定快取中沒有任何舊資料或不正確的資料。
* 預熱快取，它會預先呼叫最受歡迎或最關鍵的儲存頁面，以便產生並儲存這些頁面的快取。 此作業可以使用任何網際網路編目程式執行，或者手動執行（如果您有小型存放區）。
