---
title: '"[!DNL Upgrade Compatibility Tool] 要求'
description: '驗證您的系統是否滿足運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。 '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# 系統要求

{{commerce-only}}

使用 [!DNL Upgrade Compatibility Tool] 為：

| **要求** | **約束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 作曲家 | 無已知要求 |
| Node.js | [節點.js](https://nodejs.org/) (`^12.22.0`。 `^14.17.0`或 `>=16.0.0`) |
| 記憶體限制 | 至少2GB RAM |

您可以運行 [!DNL Upgrade Compatibility Tool] 在多個作業系統中（不支援Windows）。 你不用 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce實例所在的位置。

對於 [!DNL Upgrade Compatibility Tool] 訪問Adobe Commerce實例的原始碼。 例如，您可以將其安裝在一台伺服器上，然後將其指向另一台伺服器上的Adobe Commerce安裝。

如果您運行 [!DNL Upgrade Compatibility Tool] 對於具有大模組和檔案的Adobe Commerce實例，該工具可能需要大量RAM（至少2GB）。

## Adobe Commerce訪問密鑰

你一定有 [Adobe Commerce訪問密鑰](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 下載並使用 [!DNL Upgrade Compatibility Tool]。 將您的Adobe Commerce訪問密鑰添加到 `auth.json` 檔案，位於 `~/.composer` 預設值。

>[!WARNING]
>
>檢查 **COMPOSER_HOME** 環境變數，以查看 `auth.json` 的下界。

的 **公鑰** 與 _用戶名_ 而 **私鑰** 是 _密碼_:

### Adobe Commerce訪問密鑰示例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

## 作曲家

下載 [!DNL Upgrade Compatibility Tool] 儲存庫和運行 `composer install` 安裝依賴項。

>[!NOTE]
>
> 如果未正確配置 **Adobe Commerce訪問密鑰**，無法下載 [!DNL Upgrade Compatibility Tool]。 運行 `composer create-project` 命令將失敗。

## Node.js

要安裝Node.js，請參見Node.js [文檔](https://nodejs.dev/learn/how-to-install-nodejs)。

## 第三方擴展

Adobe建議您與擴展供應商聯繫，以確定您的擴展是否與最新版本的Adobe Commerce完全相容。
