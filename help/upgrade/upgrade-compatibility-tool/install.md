---
title: 下載 [!DNL Upgrade Compatibility Tool]
description: 按照以下步驟下載 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# 安裝 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一個命令行工具，它通過分析Adobe Commerce定制實例中安裝的所有模組來對照特定版本檢查該實例。 它返回一個錯誤和警告清單，在升級到最新版本的Adobe Commerce之前必須解決這些錯誤和警告。

## 先決條件

安裝 [!DNL Upgrade Compatibility Tool]，必須安裝必要的必備元件。

請參閱 [先決條件](../upgrade-compatibility-tool/prerequisites.md) 的子菜單。

## 下載 [!DNL Upgrade Compatibility Tool]

下載 [!DNL Upgrade Compatibility Tool]，運行以下命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Adobe Commerce訪問密鑰

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

### 作曲家

下載 [!DNL Upgrade Compatibility Tool] 儲存庫和運行 `composer install` 安裝依賴項。

>[!WARNING]
>
>如果 **Adobe Commerce訪問密鑰** 未正確配置，無法下載 [!DNL Upgrade Compatibility Tool] 當運行 `composer create-project` 命令它將失敗。

### Node.js

要安裝Node.js，請參見Node.js [文檔](https://nodejs.dev/learn/how-to-install-nodejs)。

## 第三方擴展

Adobe建議您與擴展供應商聯繫，以確定您的擴展是否與Adobe Commerce最新發佈的版本完全相容。

請參閱 [運行工具](../upgrade-compatibility-tool/run.md) 有關執行的資訊 [!DNL Upgrade Compatibility Tool]。
