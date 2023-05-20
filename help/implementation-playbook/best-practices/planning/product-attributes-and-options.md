---
title: 產品屬性配置最佳實踐
description: 瞭解如何通過限制產品屬性、屬性選項和屬性集的數量來優化Adobe Commerce效能
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# 產品屬性配置的最佳做法

- 為獲得最佳效能，請不要配置超過建議的最大產品屬性數或產品屬性選項。

- **產品屬性**—
   - 對於Adobe Commerce版本2.3.x和2.4.0到2.4.1-p1 ，配置不超過500個屬性
   - 對於Adobe Commerce版本2.4.2及更高版本，最多配置1500個產品屬性
- **產品屬性選項** — 為每個屬性配置最多100個屬性選項
- **產品屬性集** — 最多配置1000個屬性集_

>[!NOTE]
>
>產品屬性指定全局應用於所有產品的功能。 產品屬性選項是用於指定適用於特定產品的功能的自定義。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少產品屬性數

為了在從管理員管理產品並檢索儲存端的產品資料時獲得最佳效能：

- 對不同產品使用不同的產品模板（屬性集）。
- 利用定制選項和複雜產品進行變體管理
- 最小化可搜索屬性的數量。
- 刪除未使用的產品屬性。
- 在外部產品管理系統(PMS)中儲存和管理與非商業相關的屬性。

## 減少產品屬性選項的數量

為了在從管理員管理產品並檢索儲存端的產品資料時獲得最佳效能：

- 使用不同的變異機制建立產品：複雜產品、定制選項作為產品變體的來源。
- 構建具有目標屬性和選項的特定產品模板，以避免使用通用產品模板和選項容器。
- 維護實際屬性選項清單。
- 通過外部產品管理系統(PMS)管理產品資訊。

## 減少產品屬性集數

使用MySQL刪除未使用的產品屬性集。

### 查看屬性集配置

1. [連接到站點資料庫](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database)。

1. 使用MySQL查找屬性集數

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 刪除所有未使用的屬性集。

## 潛在的效能影響

配置多個 **產品屬性** 增加每個產品（EAV結構）的產品模板大小和必須檢索的資料量。 此增加會通過以下方式影響操作：

- 與EAV資料檢索相關的SQL查詢通信量增加以及處理的資料量導致資料庫吞吐量降低
- Adobe Commerce索引和全文搜索索引的大小顯著增加
- 為超大的產品模板構建FLAT索引並且無法使用時，達到MySQL的嚴格限制

增加產品資料和索引大小可能會通過以下方式影響站點效能：

- 增加了與目錄瀏覽、搜索（快速和高級）和分層導航相關的大多數店面場景的響應時間。
- 管理員中的產品管理操作非常緩慢，這可能導致超時。
- 可以阻止「產品成批活動」功能。
- 由於執行時間較長，無法每天執行中型和大型目錄的索引重建時間。

配置多個 **屬性選項** 可能通過以下方式影響站點效能：

- 對包含複雜產品的產品詳細資訊(PDP)和類別頁面的長請求和渲染時間。
- 管理產品保存操作響應時間超過最佳效能目標。
- 增加「產品編輯」表單呈現時間。
- 結帳緩慢。

## 其他資訊

- [產品屬性概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [屬性集](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [自定義教程>自定義產品建立表單](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
