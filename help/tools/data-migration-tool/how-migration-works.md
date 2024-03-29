---
title: 資料移轉的運作方式
description: 瞭解Magento1和Magento2之間的資料移轉程式，包括術語、工作流程圖表和步驟。
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# 資料移轉的運作方式

本主題提供如何使用將資料從Magento1移轉至Magento2的整體概觀。 [!DNL Data Migration Tool].

此 [!DNL Data Migration Tool] 是一個命令列介面(CLI)工具，用於將資料從Magento1傳輸到Magento2。 此工具會驗證Magento1和2資料庫結構（表格和欄位）之間的一致性、追蹤資料傳輸進度、建立記錄檔，以及執行資料驗證測試。

## 術語

* **模式**  — 將資料從Magento1.x移轉至Magento2.x的一組有序操作。
* **步驟**  — 以定義要移轉的資料型別的模式執行的工作。
* **階段**  — 驗證、傳輸及驗證資料的步驟中工作。
* **對應檔案**  — 定義Magento1.x和Magento2.x資料結構之間的規則及連線以完成階段的XML檔案。

## 模式

此 [!DNL Data Migration Tool] 將移轉程式分割成三個階段或 *模式* 以便從Magento1.x傳輸資料並調整為Magento2.x。此處列出三種模式，必須依此順序執行：

1. **設定模式**：移轉系統設定和網站相關的設定。
1. **資料模式**：大量移轉資料庫資產。
1. **差異模式**：移轉增量變更（自上次執行以來的變更），例如新客戶和訂單。

![移轉模式](../../assets/data-migration/MigrationModes2.png)

## 步驟

此 [!DNL Data Migration Tool] 使用清單 *步驟* 在每個模式中移轉特定型別的資料。 例如，在「設定」模式中，有兩個步驟可用來移轉所有設定資料：「儲存」步驟和「設定」步驟。 有關每個步驟中移轉的特定資料（以及其他模式中的步驟）的詳細資訊，請參閱 [[!DNL Data Migration Tool] 技術規格](technical-specification.md).

![移轉概述](../../assets/data-migration/MigrationOverview2.png)

## 階段

每個步驟包含三個 *階段* 這些檔案會一律以此順序執行，以確保資料會正確移轉：

1. **完整性檢查**：比較表格欄位名稱、型別和其他資訊，以驗證Magento1和2資料結構之間的相容性。
1. **資料傳輸**：從Magento1和2依表格傳輸資料表格。
1. **磁碟區檢查**：比較表格之間的記錄數，以驗證傳輸是否成功。

![移轉階段](../../assets/data-migration/MigrationSteps2.png)

## 對應檔案

移轉程式的最低層級為XML *對應檔案*. 此 [!DNL Data Migration Tool] 使用步驟階段中的對應檔案，在Magento1.x和2.x表格之間轉換不同的資料結構。

例如，當您從Magento Open Source1.8.0.0資料庫轉換資料至Magento Open Source2.x.x時，對應檔案會說明表格已重新命名的事實，並在目的地資料庫中相應地重新命名表格。 如果資料結構或資料格式沒有差異， [!DNL Data Migration Tool] 會依原狀將資料（包括擴充功能所建立之表格的資料）傳輸至Magento2資料庫。

如果未在對應檔案中宣告差異，則 [!DNL Data Migration Tool] 顯示錯誤且無法啟動。

對應檔案的詳細討論請參閱[[!DNL Data Migration Tool] 技術規格]。

## 移轉流程圖

![移轉流程](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技術規格](technical-specification.md)

我們很高興您考慮從全球的#1商業平台(Magento1.x)移至未來的平台Magento2。 我們很高興能夠分享此程式的詳細資訊，我們稱之為「移轉」。

## 移轉元件

Magento2移轉包含四個元件：資料、擴充功能和自訂程式碼、主題和自訂。

### 資料

我們已開發 **MAGENTO2[!DNL Data Migration Tool]** 協助您有效率地將所有產品、客戶和訂單資料、商店設定、促銷活動等移至Magento2。 本指南提供遷移資料的工具及最佳作法相關資訊。

### 擴充功能與自訂程式碼

我們一直與開發社群合作，協助您在Magento2中使用Magento1擴充功能。 現在，我們很榮幸地介紹 [Commerce Marketplace](https://marketplace.magento.com/)，您可在此處下載或購買最愛擴充功能的最新版本。

有關為Magento2開發擴充功能的詳細資訊，請參閱 [PHP開發人員指南](https://developer.adobe.com/commerce/php/development/).

### 主題和自訂

Magento2採用新方法和技術，讓商家擁有無與倫比的能力，可打造創新的購物體驗，並提升業務規模。 為了善用這些進階功能，開發人員必須變更其主題和自訂。 線上提供建立Magento2的檔案 [主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/)， [版面](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)、和 [自訂](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## 移轉工作

就像在1.x版本（例如，從v1.12到v1.14）之間升級一樣，從Magento1移轉至Magento2的工作量層級取決於您建立網站的方式及其自訂層級。
不過，我們不斷改善 [!DNL Data Migration Tool] (請參閱 [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) 以取得詳細資訊)；因此移轉工作會持續減少。
