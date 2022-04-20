---
title: 部署流
description: '瞭解在生產環境中部署Adobe Commerce或Magento Open Source所需的步驟。 '
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 部署流

的 [!DNL Commerce] 生產部署流幫助儲存達到最高效能。

## 安裝依賴項

的 `composer.json` 和 `composer.lock` 檔案管理 [!DNL Commerce] 依賴項，並為每個軟體包安裝相應的版本。 必須先安裝依賴項 [預處理依賴注入指令](#preprocess-dependency-injection-instructions) 如果您計畫更新 [自動載入器](#update-the-autoloader)。

安裝 [!DNL Commerce] 依賴項：

```bash
composer install --no-dev
```

## 預處理依賴項注入指令

在預處理和編譯相關性注入(DI)指令時，Magento:

* 讀取並處理所有當前配置
* 分析類之間的相關性
* 建立自動生成的檔案（包括代理、工廠等）
* 將已編譯的資料和配置儲存在快取中，在處理請求時可節省高達25%的時間

要預處理和編譯DI指令，請執行以下操作：

```bash
bin/magento setup:di:compile
```

## 更新自動載入程式

編譯完成後，確認 [已啟用APCu](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html#php-settings) 並更新自動載入程式：

要更新自動載入程式，請執行以下操作：

>[!INFO]
>
>的 `-o` 選項將PSR-0/4自動載入轉換為classmap以獲得更快的自動載入程式。 的 `--apcu` 選項使用APCu快取找到/未找到的類。

```bash
composer dump-autoload -o --apcu
```

如果計畫更新自動載入程式，則必須按順序運行以下命令：

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

部署靜態內容的原因 [!DNL Commerce] 執行以下操作：

* 分析所有靜態資源
* 執行內容合併、最小化和捆綁
* 讀取和處理主題資料
* 分析主題回退
* 將所有已處理和實體化視圖內容儲存到特定資料夾以供進一步使用

如果未部署靜態內容， [!DNL Commerce] 即時執行所有列出的操作，導致響應時間顯著增加。

您可以使用多種選項根據儲存大小和完成需求自定義部署操作。 最常見的是緊湊部署策略。 請參閱 [靜態檔案部署策略](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-static-deploy-strategies.html)

部署靜態內容：

```bash
bin/magento setup:static-content:deploy
```

此命令允許Composer重建到項目檔案的映射，以便它們載入更快。

## 設定生產模式

>[!INFO]
>
>將模式設定為生產自動運行 `setup:di:compile` 和 `setup:static-content:deploy`。

最後，您需要將您的商店置於生產模式。 生產模式已經過專門優化，可實現商店的最大效能。 它還會取消激活所有特定於開發人員的特徵。 可以在 `.htaccess` 或 `nginx.conf` 檔案：

`SetEnv MAGE_MODE production`

您還可以部署靜態內容、編譯內容，並在一個CLI命令中設定模式：

```bash
bin/magento deploy:mode:set production
```

該命令在後台運行，不允許您在每個特定步驟上設定其他選項。

## 其他發佈前操作

建議執行這些步驟，但不是強制步驟。 在生產模式下啟動商店之前，您可以立即執行這些操作。 清單包括：

* 重新編製資料索引，以避免索引中存在任何不一致的資料。
* 刷新快取，以確保快取中不留有舊資料或錯誤資料。
* 預熱快取，它會提前調用最流行或最關鍵的儲存頁，因此生成並儲存它們的快取。 此操作可以使用任何Internet Crawler執行，也可以手動執行（如果您有小商店）。
