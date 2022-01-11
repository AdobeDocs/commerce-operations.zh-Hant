---
title: 安裝升級相容性工具
description: 請依照下列步驟，安裝您Adobe Commerce專案的升級相容性工具。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# 安裝升級相容性工具

升級相容性工具是命令列工具，可分析安裝在其中的所有模組，以根據特定版本檢查Adobe Commerce自訂例項。 它會傳回在升級至最新版Adobe Commerce之前必須處理的錯誤和警告清單。

## 工作流程

下圖顯示了運行升級相容性工具時預期的工作流：

![升級相容性工具圖](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 升級相容性工具適用於誰？

以下使用案例說明Adobe Commerce合作夥伴升級用戶端執行個體的典型程式：

1. 合作夥伴的軟體工程師從 [Adobe Commerce存放庫](https://repo.magento.com/) 並在最新Adobe Commerce版本的測試階段執行。 請參閱 [下載升級相容性工具](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 主題以取得詳細資訊。
1. 軟體工程師為當前安裝的特定版本的Adobe Commerce生成一個Vanilla實例。 請參閱 [貢獻者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) ，以了解有關使用 `instance` 命令生成Vanilla安裝。
1. 軟體工程師發現清單和目錄模組中存在多個自定義區域，它們也會獲得X的複雜性分數。請參閱 [開發人員](../upgrade-compatibility-tool/developer.md) 指南，以取得複雜性分數的詳細資訊。
1. 利用此資訊，軟體工程師能夠了解升級的複雜性，並能夠將此資訊轉發回合作夥伴的客戶經理。
1. 客戶經理會建立Adobe Commerce升級的時間表和成本，以便取得經理的核准。
1. 經其經理批准後，軟體工程師將進行所需的代碼修改以修復損壞的模組。
1. 軟體工程師在Adobe Commerce搶鮮版中再次運行升級相容性工具，以確保沒有新問題，並且其代碼更改修復了測試階段發現的問題。
1. 所有項目都會結帳，軟體工程師將程式碼推送至測試環境，回歸測試會確認所有測試都是綠色的，這可讓他們在Adobe Commerce搶鮮版發行的當天，將最新的Adobe Commerce版本發佈至生產環境。

   ![升級相容性工具受眾](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Vanilla例項是針對特定版本指定版本標籤或分支的全新安裝。

## 必要條件

請參閱 [必要條件](../upgrade-compatibility-tool/prerequisites.md) 以取得更多資訊。

>[!NOTE]
>
>您可以在任何作業系統中運行升級相容性工具。 不需要執行Adobe Commerce執行個體所在的升級相容性工具。 升級相容性工具必須能存取Adobe Commerce執行個體的原始碼。 例如，您可以將工具安裝在一台伺服器上，並將它指向另一台伺服器上的Adobe Commerce安裝。

如果您對具有大模組和檔案的Adobe Commerce實例運行升級相容性工具，則該工具可能需要大量RAM，至少2GB RAM。

### 建議的動作

Adobe Commerce最佳實務建議避免有兩個模組具有相同名稱。 如果發生此情況，升級相容性工具會顯示區段錯誤。

若要避免此錯誤，建議執行 `bin` 命令及新增的選項 `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>此 `<dir>` value是您的Adobe Commerce執行個體所在的目錄。

此 `-m` 選項可讓升級相容性工具獨立分析每個特定模組，以避免在Adobe Commerce執行個體中遇到兩個名稱相同的模組。

此命令選項還允許「升級相容性工具」分析包含多個模組的資料夾：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

此建議也有助於解決執行升級相容性工具時可能發生的記憶體問題。

## 下載升級相容性工具

要下載升級相容性工具，請運行以下命令：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## 安裝

要安裝升級相容性工具，必須安裝必要的先決條件：

* Adobe Commerce存取金鑰
* 撰寫器
* Node.js

### Adobe Commerce存取金鑰

您必須 [Adobe Commerce存取金鑰](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) 下載並使用升級相容性工具。 將您的Adobe Commerce存取金鑰新增至 `auth.json` 檔案，位於 `~/.composer` 依預設。

>[!WARNING]
>
>檢查 **COMPOSER_HOME** 環境變數，查看位置 `auth.json` 檔案的位置。

此 **公開金鑰** 與 _用戶名_ 而 **私密金鑰** 是 _密碼_:

### Adobe Commerce存取金鑰範例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### 撰寫器

複製升級相容性工具儲存庫並運行 `composer install` 安裝相依性。

>[!WARNING]
>
>若 **Adobe Commerce存取金鑰** 未正確配置，升級相容性工具將不會安裝，並且在運行時，您將遇到錯誤 `composer install` 命令。

### Node.js

若要安裝Node.js，請參閱Node.js [檔案](https://nodejs.dev/learn/how-to-install-nodejs).

## 協力廠商擴充功能

Adobe建議您聯絡擴充功能廠商，判斷您的擴充功能是否與Adobe Commerce 2.4.x完全相容。

請參閱 [執行工具](../upgrade-compatibility-tool/run.md) 有關執行升級相容性工具的資訊。
