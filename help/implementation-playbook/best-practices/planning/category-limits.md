---
title: 類別配置最佳做法
description: 通過限制目錄中類別的數量來瞭解最佳做法以最大限度地提高站點效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 類別配置的最佳做法

為獲得最佳效能，請不要為Adobe Commerce站點配置超過建議的最大類別數。

- 對於Adobe Commerce版本2.4.2及更高版本，最多配置6000個類別
- 對於Adobe Commerce版本2.3.x和2.4.0至2.4.1-p1，最多配置3000個類別

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少產品數量

使用以下策略減少類別數：

- 通過屬性和自定義選項管理獨特的產品功能
- 刪除非活動類別
- 優化導航中的目錄深度

## 潛在的效能影響

超過建議的最大類別數可能會通過以下方式影響站點效能：

- 非快取目錄頁響應時間的明顯增加
- 在管理管理員中管理類別時執行和超時時間長
- 相應資料庫表的大小增加
- 較大的索引表增加了完成對 `[category/product relation index\]`
- 增加處理時間以完成類別樹構建、菜單檢索和類別規則管理操作

## 其他資訊

- [類別概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [導航概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [產品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce在雲基礎架構方面：儲存配置的最佳做法](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
