---
title: 類別設定最佳實務
description: 了解最佳實務，限制目錄中的類別數目，以發揮網站效能最大。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 類別設定最佳作法

為獲得最佳效能，請勿為Adobe Commerce網站設定超過建議的最大類別數。

- 若為Adobe Commerce 2.4.2版和更新版本，最多可設定6000個類別
- 若為Adobe Commerce 2.3.x版和2.4.0至2.4.1-p1版，最多可設定3000個類別

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少產品數量

使用下列策略來減少類別數：

- 透過屬性和自訂選項管理獨特的產品功能
- 移除非作用中類別
- 在導覽中最佳化目錄深度

## 潛在績效影響

超過建議的最大類別數量，可透過下列方式影響網站效能：

- 非快取目錄頁面回應時間的顯著增加
- 從管理員管理類別時執行時間長和逾時
- 相應資料庫表的大小增加
- 較大的索引表增加了完成索引操作所需的時間 `[category/product relation index\]`
- 增加處理時間，以完成類別樹構建、菜單檢索和類別規則管理操作

## 其他資訊

- [類別概觀](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [導覽概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [產品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce雲基礎架構：儲存配置最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
