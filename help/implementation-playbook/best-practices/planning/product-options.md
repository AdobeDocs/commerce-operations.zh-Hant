---
title: 產品選項設定最佳實務
description: 限制產品選項數量，以最佳化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 產品選項最佳實務

為獲得最佳效能，每個產品最多配置100個產品選項。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少產品選項

為獲得最佳網站效能，請使用下列策略來減少產品選項的數量：

- 將複雜產品和自訂選項設定為產品變異的來源。
- 使用屬性集來建立具有目標屬性和選項的特定產品模板，而不是建立適用於所有產品的全局產品模板和選項容器。
- 通過外部產品管理系統(PMS)管理產品資訊。

## 潛在的效能影響

配置許多產品選項會增加每個產品在所有讀和寫操作上檢索的資料量，從而導致：

- 增加的SQL查詢流量和更重的 `JOIN` 操作提高了資料庫吞吐量。
- 增加Adobe Commerce索引和全文搜尋索引的大小。

以上列出的增加可能會透過下列方式影響網站效能：

- 與屬性中包含許多選項的產品相關的大多數店面案例的回應時間較長。
- 在管理員中完成產品管理操作所需的時間大幅增加，這可能導致逾時，尤其是與屬性清單和樹狀檢索（包括促銷規則管理）相關的案例。
- 可以阻止完成非同步成批操作的批量操作，如導入和導出，以及將自定義價格分配給共用目錄中的多個產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品屬性設定最佳實務](product-attributes-and-options.md)
- [大量動作記錄](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [庫存成批操作API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [培訓：使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

