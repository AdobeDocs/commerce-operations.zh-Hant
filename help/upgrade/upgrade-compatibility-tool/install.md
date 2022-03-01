---
title: 安裝 [!DNL Upgrade Compatibility Tool]
description: 按照以下步驟安裝 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: 317a044e66fe796ff66b9d8cf7b308f741eb82c1
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# 安裝 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一個命令行工具，它通過分析Adobe Commerce定制實例中安裝的所有模組來對照特定版本檢查該實例。 它返回一個錯誤和警告清單，在升級到最新版本的Adobe Commerce之前必須解決這些錯誤和警告。

## 工作流

下圖顯示了運行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 圖](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 誰是 [!DNL Upgrade Compatibility Tool] 為什麼？

以下用例描述了Adobe Commerce合作夥伴升級客戶端實例的典型過程：

1. 合作夥伴的軟體工程師下載 [!DNL Upgrade Compatibility Tool] 包 [Adobe Commerce庫](https://repo.magento.com/) 並在最新Adobe Commerce版的測試階段執行。 查看 [下載 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 的子菜單。
1. 軟體工程師為當前安裝的特定版本的Adobe Commerce生成一個香草實例。 查看 [貢獻者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 的子菜單。 `instance` 命令生成香草安裝。
1. 軟體工程師發現清單和目錄模組中有幾個自定義區域已損壞，並且它們還得到複雜性分數X。查看 [開發人員](../upgrade-compatibility-tool/developer.md) 的子菜單。
1. 利用這些資訊，軟體工程師能夠瞭解升級的複雜性，並能夠將此資訊轉回合作夥伴的客戶經理。
1. 客戶經理為Adobe Commerce升級建立時間表和成本，以便他們獲得經理的批准。
1. 經經理批准後，軟體工程師將根據需要進行的代碼修改來修復損壞的模組。
1. 軟體工程師運行 [!DNL Upgrade Compatibility Tool] 再使用一次Adobe Commerce預發行版，以確保沒有新問題，並且其代碼更改會修復測試階段發現的問題。
1. 所有內容都會檢查，軟體工程師將代碼推送到分段環境，在分段環境中，回歸test確認所有test都是綠色的，這使他們能夠在Adobe Commerce預發佈的同一天將最新的Adobe Commerce版本發佈到生產環境中。

   ![[!DNL Upgrade Compatibility Tool] 觀眾](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Vanilla實例是指特定版本的指定版本標籤或分支的全新安裝。

## 先決條件

請參閱 [先決條件](../upgrade-compatibility-tool/prerequisites.md) 的子菜單。

>[!NOTE]
>
>您可以運行 [!DNL Upgrade Compatibility Tool] 在任何作業系統中。 不需要運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce實例所在的位置。 對於 [!DNL Upgrade Compatibility Tool] 訪問Adobe Commerce實例的原始碼。 例如，您可以在一台伺服器上安裝該工具，並將其指向另一台伺服器上的Adobe Commerce安裝。

如果您運行 [!DNL Upgrade Compatibility Tool] 對於具有大模組和檔案的Adobe Commerce實例，該工具可能需要大量RAM，至少需要2GB RAM。

### 建議的操作

Adobe Commerce最佳做法建議避免使用兩個同名模組。 如果發生這種情況， [!DNL Upgrade Compatibility Tool] 顯示分段錯誤。

為避免此錯誤，建議運行 `bin` 命令和添加的選項 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>的 `<dir>` value是您的Adobe Commerce實例所在的目錄。

的 `-m` 選項 [!DNL Upgrade Compatibility Tool] 獨立分析每個特定模組，以避免在Adobe Commerce實例中遇到兩個同名模組。

此命令選項還允許 [!DNL Upgrade Compatibility Tool] 要分析包含多個模組的資料夾：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

此建議還有助於解決執行 [!DNL Upgrade Compatibility Tool]。

## 下載 [!DNL Upgrade Compatibility Tool]

下載 [!DNL Upgrade Compatibility Tool]，運行以下命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 安裝

安裝 [!DNL Upgrade Compatibility Tool]，必須安裝必要的必備元件：

* Adobe Commerce訪問密鑰
* 作曲家
* Node.js

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

克隆 [!DNL Upgrade Compatibility Tool] 儲存庫和運行 `composer install` 安裝依賴項。

>[!WARNING]
>
>如果 **Adobe Commerce訪問密鑰** 未正確配置， [!DNL Upgrade Compatibility Tool] 將不安裝，運行時將出現錯誤 `composer install` 的子菜單。

### Node.js

要安裝Node.js，請參見Node.js [文檔](https://nodejs.dev/learn/how-to-install-nodejs)。

## 第三方擴展

Adobe建議您與擴展供應商聯繫，以確定擴展是否與Adobe Commerce2.4.x完全相容。

請參閱 [運行工具](../upgrade-compatibility-tool/run.md) 有關執行的資訊 [!DNL Upgrade Compatibility Tool]。
