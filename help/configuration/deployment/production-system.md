---
title: 生產系統設定
description: 了解如何為商務應用程式設定生產系統。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# 生產系統設定

您可以有一個生產系統。 以下所有條件必須為true:

- 所有商務代碼都與開發和構建系統位於同一儲存庫的原始碼控制中
- 請確定下列所有事項 _包含_ 在原始碼控制項中：

   - `app/etc/config.php`
   - `generated` 目錄（和子目錄）
   - `pub/media` 目錄
   - `pub/media/wysiwyg` 目錄（和子目錄）
   - `pub/static` 目錄（和子目錄）

- 必須安裝Commerce 2.2或更新版本，並針對 [生產模式](../bootstrap/application-modes.md#production-mode)
- 它具有檔案系統所有權和權限集，如 [開發、建置和生產系統的先決條件](../deployment/prerequisites.md).

## 設定生產機器

要設定生產機器，請執行以下操作：

1. 安裝商務或從原始碼控制項拉取商務後，以或切換至 [檔案系統所有者](https://glossary.magento.com/magento-file-system-owner).
1. 建立 `~/.ssh/.composer/auth.json` 如果您尚未這麼做。

   建立目錄：

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   建立 `auth.json` 在目錄中。

   `auth.json` 必須包含 [驗證金鑰](../../installation/prerequisites/authentication-keys.md).

   範例如下：

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

1. 將變更儲存至 `auth.json`.
1. 複製 `<Commerce root dir>/app/etc/env.php` 從您的開發系統到生產系統。
1. 開啟 `env.php` 在文字編輯器中變更任何必要值（例如資料庫連線資訊）。
1. 執行 [`magento config:set`](../cli/set-configuration-values.md) 或 [`magento config:set-sensitive`](../cli/set-configuration-values.md) 命令，分別設定任何系統特定或敏感配置值的值。

   以下章節顯示範例。

## 在生產系統上設定配置值

本節探討如何使用 `magento config:sensitive:set` 命令。

若要設定敏感值：

1. 尋找要使用 [敏感值參考](../reference/config-reference-sens.md).
1. 記下設定的設定路徑。
1. 以檔案系統所有者身份或切換到該檔案系統所有者身份登錄到生產系統。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   例如，若要將YouTube API金鑰的值設為 `1234`，輸入

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   您也可以互動式設定一或多個值，如下所示：

   ```bash
   bin/magento config:sensitive:set -i
   ```

   出現提示時，請為每個敏感設定輸入一個值，或按Enter鍵跳過一個值，然後移至下一個值。

1. 若要確認值已設定，請登入管理員。
1. 在「管理員」中找到設定。

   例如，YouTube API金鑰設定位於 **商店** >設定> **設定** > **目錄** > **目錄** > **產品影片**.

   設定會顯示在「管理員」中，且無法編輯。 下圖顯示了一個示例。

   ![管理中的敏感設定](../../assets/configuration/sensitive-set.png)
