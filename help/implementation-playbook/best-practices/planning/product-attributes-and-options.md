---
title: 產品屬性設定最佳實務
description: 了解如何限制產品屬性、屬性選項和屬性集的數量，以最佳化Adobe Commerce效能
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 產品屬性設定最佳實務

- 為獲得最佳效能，請不要配置超過建議的最大產品屬性數或產品屬性選項數。

- **產品屬性**—
   - 若為Adobe Commerce 2.3.x版和2.4.0至2.4.1-p1版，請不要設定超過500個屬性
   - 針對Adobe Commerce 2.4.2版和更新版本，請設定最多1500個產品屬性
- **產品屬性選項** — 為每個屬性配置最多100個屬性選項
- **產品屬性集** — 配置最多1000個屬性集_

>[!NOTE]
>
>產品屬性會指定全域套用至所有產品的功能。 產品屬性選項是自訂項目，可指定套用至特定產品的功能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少產品屬性數

為了在從管理員管理產品並擷取店面中的產品資料時提供最佳效能：

- 對不同產品使用不同的產品範本（屬性集）。
- 運用自訂選項和複雜產品來管理變數
- 將可搜尋屬性的數量減到最少。
- 移除未使用的產品屬性。
- 在外部產品管理系統(PMS)中儲存和管理與非商務相關的屬性。

## 減少產品屬性選項數

為了在從管理員管理產品並擷取店面中的產品資料時提供最佳效能：

- 使用不同的變異機制來建立產品：複雜產品，自訂選項，作為產品變異的來源。
- 使用定位屬性和選項建立特定產品範本，以避免使用廣義的產品範本和選項容器。
- 維護實際屬性選項的清單。
- 通過外部產品管理系統(PMS)管理產品資訊。

## 減少產品屬性集數

使用MySQL刪除未使用的產品屬性集。

### 查看屬性集配置

1. [連接到站點資料庫](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. 使用MySQL查找屬性集的數量

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 移除任何未使用的屬性集。

## 潛在績效影響

設定許多 **產品屬性** 增加每個產品的產品範本大小（EAV結構），以及必須擷取的資料量。 此增加會透過下列方式影響操作：

- 與EAV資料檢索相關的SQL查詢流量的增加以及處理的資料量，這導致DB吞吐量的降低
- Adobe Commerce索引和全文搜尋索引的大小大幅增加
- 為超大的產品模板建立FLAT索引時，並且無法使用它時，會達到MySQL的嚴格限制

產品資料和索引大小增加可能會透過下列方式影響網站效能：

- 增加與目錄瀏覽、搜尋（快速和進階）及分層導覽相關的大部分店面案例的回應時間。
- 管理員中的產品管理作業會顯著緩慢，而可能導致逾時。
- 可以阻止「產品批量操作」功能。
- 由於執行時間過長，無法每天執行中型和大型目錄的索引重建時間。

設定許多 **屬性選項** 可能會以下列方式影響網站效能：

- 包含複雜產品的產品詳細資訊(PDP)和類別頁面的要求和轉譯時間過長。
- 管理員產品節省操作響應時間超過最佳效能目標。
- 增加產品編輯表單轉譯時間。
- 結帳緩慢。

## 其他資訊

- [產品屬性概觀](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [屬性集](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [自訂教學課程>自訂產品建立表單](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

