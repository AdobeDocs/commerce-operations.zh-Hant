---
title: 資料移轉的運作方式
description: 瞭解Magento 1與Magento 2之間的資料移轉程式，包括術語、工作流程圖表和步驟。
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# 資料移轉的運作方式

本主題提供如何使用[!DNL Data Migration Tool]將資料從Magento 1移轉至Magento 2的整體概觀。

[!DNL Data Migration Tool]是命令列介面(CLI)工具，用於將資料從Magento 1傳輸至Magento 2。 此工具會驗證Magento 1和2資料庫結構（表格和欄位）之間的一致性、追蹤資料傳輸進度、建立記錄檔，以及執行資料驗證測試。

## 術語

* **模式** — 將資料從Magento 1.x移轉至Magento 2.x的一組有序作業。
* **步驟** — 模式中的工作，定義要移轉的資料型別。
* **階段** — 步驟中驗證、傳輸及驗證資料的工作。
* **對應檔案** — 定義Magento 1.x和Magento 2.x資料結構之間的規則和連線的XML檔案，用於完成階段。

## 模式

[!DNL Data Migration Tool]將移轉程式分割成三個階段或&#x200B;*模式*，以便從Magento 1.x傳輸資料並調整為Magento 2.x。此處列出三種模式，必須依此順序執行：

1. **設定模式**：移轉系統組態和網站相關設定。
1. **資料模式**：大量移轉資料庫資產。
1. **差異模式**：移轉增量變更（自上次執行以來的變更），例如新客戶和訂單。

![移轉模式](../../assets/data-migration/MigrationModes2.png)

## 步驟

[!DNL Data Migration Tool]在每個模式中使用包含&#x200B;*個步驟*&#x200B;的清單來移轉特定型別的資料。 例如，在「設定」模式中，有兩個步驟可用來移轉所有設定資料：「儲存」步驟和「設定」步驟。 有關每個步驟中移轉的特定資料（以及其他模式中的步驟）的詳細資訊，請參閱[[!DNL Data Migration Tool] 技術規格](technical-specification.md)。

![移轉總覽](../../assets/data-migration/MigrationOverview2.png)

## 階段

每個步驟內都有三個&#x200B;*階段*，一律以此順序執行，以確保資料正確移轉：

1. **完整性檢查**：比較資料表欄位名稱、型別和其他資訊，以驗證Magento 1和2資料結構之間的相容性。
1. **資料傳輸**：從Magento 1和2依資料表傳輸資料表。
1. **磁碟區檢查**：比較資料表之間的記錄數目，以驗證傳輸是否成功。

![移轉階段](../../assets/data-migration/MigrationSteps2.png)

## 對應檔案

移轉程式的最低層級為XML *對應檔*。 [!DNL Data Migration Tool]會在步驟的階段中使用對應檔案，在Magento 1.x和2.x表格之間轉換不同的資料結構。

例如，將資料從Magento Open Source 1.8.0.0資料庫轉換為Magento Open Source 2.x.x時，對應檔案會說明資料表已重新命名，並在目的地資料庫中相應地重新命名。 如果資料結構或資料格式沒有差異，[!DNL Data Migration Tool]會依原樣將資料傳輸至Magento 2資料庫，包括擴充功能建立的表格資料。

如果未在對應檔案中宣告差異，則[!DNL Data Migration Tool]會顯示錯誤且不會啟動。

對應檔案的詳細討論請參閱[[!DNL Data Migration Tool]技術規格]。

## 移轉流程圖

![移轉流程](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool]技術規格](technical-specification.md)

我們很高興您考慮從全球的#1商業平台Magento 1.x邁向未來的平台Magento 2。 我們很高興能夠分享此程式的詳細資訊，我們稱之為「移轉」。

## 移轉元件

Magento 2移轉包含四個元件：資料、擴充功能和自訂程式碼、主題和自訂。

### 資料

我們已開發&#x200B;**Magento 2[!DNL Data Migration Tool]**，協助您有效率地將您的所有產品、客戶和訂單資料、商店設定、促銷活動等移至Magento 2。 本指南提供遷移資料的工具及最佳作法相關資訊。

### 擴充功能與自訂程式碼

我們一直與開發社群合作，協助您在Magento 2中使用Magento 1擴充功能。 現在我們自豪地推出[Commerce Marketplace](https://commercemarketplace.adobe.com//)，您可以在其中下載或購買您最愛擴充功能的最新版本。

有關為Magento 2開發擴充功能的詳細資訊，請參閱[PHP開發人員指南](https://developer.adobe.com/commerce/php/development/)。

### 主題和自訂

Magento 2運用新方法和技術，為商戶提供無可比擬的能力，以建立創新的購物體驗，並擴展至新的境界。 為了善用這些進階功能，開發人員必須變更其主題和自訂。 線上提供建立Magento 2 [主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/)、[配置](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)和[自訂專案](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/)的檔案。

## 移轉工作

就像在1.x版本（例如從v1.12到v1.14）之間升級一樣，從Magento 1移轉至Magento 2的工作量層級取決於您建立網站的方式及其自訂層級。
不過，我們正在持續改善[!DNL Data Migration Tool] （如需詳細資訊，請參閱[變更記錄檔](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md)）；因此移轉工作會持續減少。
