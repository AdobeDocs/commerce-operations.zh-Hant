---
title: 產品選項配置最佳做法
description: 通過限制產品選項數來優化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 產品選項最佳實踐

為獲得最佳效能，請為每個產品配置最多100個產品選項。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少產品選項

為獲得最佳站點效能，請使用以下策略減少產品選項的數量：

- 將複雜產品和定制選項配置為產品變體的來源。
- 不使用建立應用於所有產品的全局產品模板和選項容器，而是使用屬性集構建具有目標屬性和選項的特定產品模板。
- 通過外部產品管理系統(PMS)管理產品資訊。

## 潛在效能影響

配置許多產品選項會增加在所有讀寫操作中為每個產品檢索的資料量，結果是：

- SQL查詢通信量增加且更重 `JOIN` 操作會提高資料庫吞吐量。
- 增加了Adobe Commerce索引和全文搜索索引的大小。

上面列出的增加可能會通過以下方式影響站點效能：

- 與屬性中包含許多選項的產品相關的大多數店面方案的響應時間更長。
- 在管理員中完成產品管理操作所需的時間顯著增加，這可能導致超時，特別是與屬性清單和樹檢索（包括升級規則管理）相關的情形。
- 可以阻止完成非同步成批操作的批量操作，例如導入和導出，以及將自定義價格分配給共用目錄中的多個產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品屬性配置的最佳做法](product-attributes-and-options.md)
- [批量操作日誌](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [庫存成批活動API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [培訓：使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
