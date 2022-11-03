---
title: 產品清單分頁的最佳實務
description: 了解如何管理店面目錄每個頁面上顯示的產品數量，以最佳化Adobe Commerce效能。
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 產品清單分頁的最佳實務

為獲得最佳效能，每頁最多顯示48種產品。

您可以設定Adobe Commerce，讓購物者在單一頁面上檢視所有類別產品。 如果類別產品的數量顯著超過48個產品，請更新店面分頁控制項的目錄設定。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 更新產品清單設定

如果任何類別中有超過48種產品，請更新店面目錄設定，以停用 **每頁允許所有產品**.

停用此選項後，Adobe Commerce會使用產品清單店面分頁控制項來管理店面元件中顯示的產品數量。 如需指示，請參閱 [設定分頁控制項](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 其他資訊

- [設定產品清單](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
