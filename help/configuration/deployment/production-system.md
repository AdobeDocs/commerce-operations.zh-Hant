---
title: 生產系統設定
description: 瞭解如何為Commerce應用程式設定生產系統。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# 生產系統設定

你可以有一個生產系統。 以下所有內容必須為真：

- 所有Commerce代碼都位於開發和構建系統所在的同一儲存庫中
- 確保以下所有內容 _包括_ 在原始碼管理中：

   - `app/etc/config.php`
   - `generated` 目錄（和子目錄）
   - `pub/media` 目錄
   - `pub/media/wysiwyg` 目錄（和子目錄）
   - `pub/static` 目錄（和子目錄）

- 必須安裝Commerce 2.2或更高版本，並為 [生產模式](../bootstrap/application-modes.md#production-mode)
- 它具有檔案系統所有權和權限集，如中所述 [開發、構建和生產系統的先決條件](../deployment/prerequisites.md)。

## 設定生產機

要設定生產機器：

1. 安裝Commerce或從原始碼管理中提取它後，以或切換到 [檔案系統所有者](https://glossary.magento.com/magento-file-system-owner)。
1. 建立 `~/.ssh/.composer/auth.json` 如果你還沒做。

   建立目錄：

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   建立 `auth.json` 目錄中。

   `auth.json` 必須包含 [身份驗證密鑰](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)。

   示例如下：

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 將更改保存到 `auth.json`。
1. 複製 `<Commerce root dir>/app/etc/env.php` 從開發系統到生產系統。
1. 開啟 `env.php` 在文本編輯器中更改任何必需的值（例如，資料庫連接資訊）。
1. 運行 [`magento config:set`](../cli/set-configuration-values.md) 或 [`magento config:set-sensitive`](../cli/set-configuration-values.md) 命令，分別設定任何系統特定或敏感配置值的值。

   以下部分顯示了一個示例。

## 在生產系統上設定配置值

本節討論如何使用 `magento config:sensitive:set` 的子菜單。

要設定敏感值：

1. 查找要使用 [敏感值參考](../reference/config-reference-sens.md)。
1. 請注意設定的配置路徑。
1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到生產系統。
1. 更改為Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例如，將YouTubeAPI鍵的值設定為 `1234`輸入

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   還可以按如下方式交互設定一個或多個值：

   ```bash
   bin/magento config:sensitive:set -i
   ```

   出現提示時，為每個敏感設定輸入一個值，或按Enter跳過一個值並移到下一個值。

1. 要驗證是否設定了值，請登錄到Admin。
1. 在管理員中查找設定。

   例如，YouTubeAPI密鑰設定位於 **商店** >設定> **配置** > **目錄** > **目錄** > **產品視頻**。

   該設定顯示在管理員中，無法編輯。 下圖顯示了一個示例。

   ![管理員中的敏感設定](../../assets/configuration/sensitive-set.png)
