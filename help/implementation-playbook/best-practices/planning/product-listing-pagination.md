---
title: 產品清單分頁的最佳做法
description: 瞭解如何通過管理顯示在店面目錄每頁上的產品數量來優化Adobe Commerce的效能。
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 產品清單分頁的最佳做法

為獲得最佳效能，每頁最多顯示48種產品。

您可以配置Adobe Commerce，使購物者能夠在單個頁面上查看所有類別產品。 如果類別產品的數量顯著超過48種產品，請更新庫面分頁控制的目錄配置。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 更新產品清單配置

如果任何類別中有超過48種產品，請更新店面目錄配置以禁用選項 **每頁允許所有產品**。

禁用此選項後，Adobe Commerce使用產品清單店面分頁控制項來管理店面元件中顯示的產品數量。 有關說明，請參見 [配置分頁控制項](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls)。

## 其他資訊

- [配置產品清單](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
