---
title: 部署流程
description: 了解在生產環境中部署Adobe Commerce或Magento Open Source所需的步驟。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# 部署流程

此 [!DNL Commerce] 生產部署流程可協助存放區達到最佳效能。

## 安裝相依性

此 `composer.json` 和 `composer.lock` 檔案管理 [!DNL Commerce] 相依性，並為每個套件安裝適當的版本。 您必須先安裝相依性 [預處理依賴注入指令](#preprocess-dependency-injection-instructions) 如果您打算更新 [自動載入器](#update-the-autoloader).

安裝 [!DNL Commerce] 相依性：

```bash
composer install --no-dev
```

## 預處理依賴注入指令

在預處理和編譯相關性插入(DI)指令時，Magento:

* 讀取並處理所有當前配置
* 分析類之間的依賴關係
* 建立自動生成的檔案（包括代理、工廠等）
* 將已編譯的資料和配置儲存在快取中，可節省高達25%的請求處理時間

要預處理和編譯DI指令，請執行以下操作：

```bash
bin/magento setup:di:compile
```

## 更新自動載入器

編譯完成後，請確認 [已啟用APCu](../performance/software.md#php-settings) 並更新自動載入器：

要更新自動載入器，請執行以下操作：

>[!INFO]
>
>此 `-o` option可將PSR-0/4自動載入轉換為classmap，以獲得更快的自動載入器。 此 `--apcu` 選項使用APCu快取找到/找不到類。

```bash
composer dump-autoload -o --apcu
```

如果您計畫更新自動載入程式，則必須按順序運行以下命令：

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

部署靜態內容原因 [!DNL Commerce] 執行下列動作：

* 分析所有靜態資源
* 執行內容合併、最小化和捆綁
* 讀取和處理主題資料
* 分析主題回退
* 將所有已處理和實體化內容儲存到特定資料夾以供進一步使用

如果未部署靜態內容， [!DNL Commerce] 即時執行所有列出的操作，導致響應時間顯著增加。

您可以根據儲存大小和完成需求使用多種選項自定義部署操作。 最常見的是精簡部署策略。 請參閱 [靜態檔案部署策略](../configuration/cli/static-view-file-strategy.md)

要部署靜態內容：

```bash
bin/magento setup:static-content:deploy
```

此命令可讓撰寫器重建對應至專案檔案，以加快其載入速度。

## 設定生產模式

>[!INFO]
>
>將模式設定為生產模式會自動執行 `setup:di:compile` 和 `setup:static-content:deploy`.

最後，您需要將商店置於生產模式。 生產模式已經過專門優化，以實現儲存的最大效能。 它也會停用所有開發人員專屬的功能。 您可以在 `.htaccess` 或 `nginx.conf` 檔案：

`SetEnv MAGE_MODE production`

您還可以部署靜態內容、編譯內容，並在一個CLI命令中設定模式：

```bash
bin/magento deploy:mode:set production
```

命令會在背景執行，不允許您在每個特定步驟上設定其他選項。

## 其他啟動前動作

建議您執行這些步驟，但非必要步驟。 您可以在以生產模式啟動商店之前立即執行這些操作。 清單包括：

* 重新索引資料，以避免索引中出現任何不一致的資料。
* 排清快取，確保快取中沒有保留任何舊資料或錯誤資料。
* 預熱快取，它提前調用最熱門或最關鍵的儲存頁，以便生成並儲存它們的快取。 此操作可以使用任何Internet Crawler執行，或者手動執行（如果您有小型商店）。
