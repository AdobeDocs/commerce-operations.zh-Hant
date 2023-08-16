---
title: 產品屬性設定最佳實務
description: 瞭解如何透過限制產品屬性、屬性選項和屬性集的數量來最佳化Adobe Commerce效能
role: User, Admin
feature: Best Practices, Catalogs
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# 產品屬性設定的最佳實務

- 為獲得最佳效能，請勿設定超過建議的最大產品屬性數或產品屬性選項數。

- **產品屬性**—
   - 若為Adobe Commerce 2.3.x版和2.4.0至2.4.1-p1版，請勿設定超過500個屬性
   - 若是Adobe Commerce 2.4.2版或更新版本，請設定最多1500個產品屬性
- **產品屬性選項** — 為每個屬性設定最多100個屬性選項
- **產品屬性集** — 最多設定1000個屬性集_
>[!NOTE]
>
>產品屬性會指定全域套用至所有產品的功能。 產品屬性選項是自訂，用於指定適用於特定產品的功能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少產品屬性數量

為獲得最佳效能，從管理員管理產品並擷取店面的產品資料：

- 針對不同的產品使用不同的產品範本（屬性集）。
- 利用自訂選項和複雜產品進行變數管理
- 將可搜尋屬性的數量減到最少。
- 移除未使用的產品屬性。
- 在外部產品管理系統(PMS)中儲存和管理非商務相關屬性。

## 減少產品屬性選項的數目

為獲得最佳效能，從管理員管理產品並擷取店面的產品資料：

- 使用不同的變異機制來建立產品：複雜的產品、作為產品變異來源的自訂選項。
- 使用目標屬性和選項建置特定的產品範本，以避免一般化的產品範本和選項容器。
- 維護實際屬性選項的清單。
- 透過外部產品管理系統(PMS)管理產品資訊。

## 減少產品屬性集數目

使用MySQL移除未使用的產品屬性集。

### 檢閱屬性集組態

1. [連線到站台資料庫](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. 使用MySQL尋找屬性集數目

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 移除任何未使用的屬性集。

## 對效能的潛在影響

設定多個 **產品屬性** 增加每個產品的產品範本大小（EAV結構），以及必須擷取的資料量。 這項增加會以下列方式影響作業：

- 與EAV資料擷取相關的SQL查詢流量增加，以及處理的資料量增加，導致DB輸送量減少
- Adobe Commerce索引和全文檢索搜尋索引的大小大幅增加
- 為超大產品範本建立FLAT索引且無法使用時，達到嚴格的MySQL限制

產品資料和索引大小的增加可能會透過下列方式影響網站效能：

- 針對與目錄瀏覽、搜尋（快速和進階）和分層導覽相關的大多數店面情境，增加回應時間。
- 管理員中的產品管理作業速度太慢，可能會造成逾時。
- 可以封鎖「產品整批動作」功能。
- 由於執行時間長，無法每天執行中型及大型目錄的索引重新建置時間。

設定多個 **屬性選項** 可能會以下列方式影響網站效能：

- 產品詳細資料(PDP)和包含複雜產品的類別頁面上的長請求和呈現時間。
- 管理產品儲存作業回應時間會增加到最佳效能目標以上。
- 增加「產品編輯」表單轉譯時間。
- 結帳緩慢。

## 其他資訊

- [產品屬性概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [屬性集](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [自訂教學課程>自訂產品建立表單](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
