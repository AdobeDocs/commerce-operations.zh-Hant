---
title: 資料移轉的運作方式
description: 了解Magento1和Magento2之間的資料移轉程式，包括術語、工作流程圖表和步驟。
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# 資料移轉的運作方式

本主題概略說明如何使用將資料從Magento1移轉至Magento2 [!DNL Data Migration Tool].

此 [!DNL Data Migration Tool] 是命令行介面(CLI)工具，用於將資料從Magento1傳輸到Magento2。 該工具驗證Magento1和2資料庫結構（表和欄位）之間的一致性，跟蹤資料傳輸進度，建立日誌，並運行資料驗證測試。

## 術語

* **模式**  — 從Magento1.x將資料移轉至Magento2.x的有序操作集。
* **步驟**  — 定義要遷移的資料類型的模式中的任務。
* **階段**  — 驗證、傳輸和驗證資料的步驟中的任務。
* **映射檔案**  — 定義Magento1.x和Magento2.x資料結構之間的規則和連接以完成這些階段的XML檔案。

## 模式

此 [!DNL Data Migration Tool] 將移轉程式分為三個階段或 *模式* 以便將資料從Magento1.x傳輸及調整至Magento2.x。這裡列出了三種模式，必須依此順序執行：

1. **設定模式**:遷移系統配置和與網站相關的設定。
1. **資料模式**:大量遷移資料庫資產。
1. **增量模式**:遷移增量更改（自上次運行以來的更改），如新客戶和訂單。

![移轉模式](../../assets/data-migration/MigrationModes2.png)

## 步驟

此 [!DNL Data Migration Tool] 使用 *步驟* 以移轉特定類型的資料。 例如，在「設定」模式中，有兩個步驟用來移轉所有設定資料：儲存步驟和設定步驟。 有關在這些步驟（以及其他模式中的步驟）中移轉的特定資料的詳細資訊，請參閱 [[!DNL Data Migration Tool] 技術規範](technical-specification.md).

![移轉概述](../../assets/data-migration/MigrationOverview2.png)

## 階段

每個步驟中有三個 *階段* 會一律執行，以確保資料正確移轉：

1. **完整性檢查**:比較表欄位名稱、類型和其他資訊，以驗證Magento1和2資料結構之間的相容性。
1. **資料傳輸**:從Magento1和2按表傳輸資料表。
1. **卷檢查**:比較表之間的記錄數，以驗證傳輸是否成功。

![遷移階段](../../assets/data-migration/MigrationSteps2.png)

## 映射檔案

在遷移過程的最低級別是XML *映射檔案*. 此 [!DNL Data Migration Tool] 在步驟的階段內使用映射檔案，在Magento1.x和2.x表之間轉換不同的資料結構。

例如，將資料從Magento Open Source1.8.0.0資料庫轉換為Magento Open Source2.x.x時，映射檔案會說明表已更名的事實，並在目標資料庫中相應地重新命名該表。 若資料結構或資料格式並無差異，則 [!DNL Data Migration Tool] 將資料按原樣傳輸至Magento2資料庫，包括由擴充功能建立之表格的資料。

若未在映射檔案中宣告差異，則 [!DNL Data Migration Tool] 顯示錯誤且未啟動。

在[中將更詳細地討論映射檔案[!DNL Data Migration Tool] 技術規範]。

## 移轉流程圖

![移轉流程](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技術規範]:technical-specification.md

我們很高興您考慮從全球#1商務平台(Magento1.x)轉向未來平台(Magento2)。 我們很高興能分享此程式的詳細資訊，我們稱之為移轉。

## 移轉元件

Magento2移轉包含四個元件：資料、擴充功能及自訂程式碼、主題和自訂。

### 資料

我們開發了 **Magento2[!DNL Data Migration Tool]** 可協助您有效地將所有產品、客戶和訂單資料、儲存設定、促銷活動等移動至Magento2。 本指南提供使用工具移轉資料的相關資訊和最佳實務。

### 擴充功能與自訂程式碼

我們一直與開發社群合作，協助您使用Magento2中的Magento1擴充功能。 現在，我們很自豪地介紹 [Commerce Marketplace](https://marketplace.magento.com/)，您可以在此下載或購買您最喜愛的擴充功能最新版本。

如需開發Magento2擴充功能的詳細資訊，請參閱 [PHP開發人員指南](https://developer.adobe.com/commerce/php/development/).

### 主題和自訂

Magento2採用新方法和技術，讓商戶擁有無與倫比的能力，創造創新的購物體驗，並擴展至新的層次。 為了利用這些進步，開發人員必須對其主題和定制進行更改。 可線上取得建立Magento2的檔案 [主題](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [版面](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)，和 [自訂](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## 移民工作

就像1.x版之間的升級（例如從1.12版移轉至1.14版）一樣，從Magento1移轉至Magento2的工作量程度取決於您建立網站的方式及其自訂程度。
然而，我們持續改善 [!DNL Data Migration Tool] (請參閱 [變更記錄](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) 詳情);因此，移民工作不斷減少。
