---
title: 產品變數設定最佳實務
description: 了解如何限制已設定的產品變數數量，以最佳化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 設定產品變體的最佳實務

為獲得最佳效能，請為每個產品配置最多50個變體。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 減少產品變異數

為獲得最佳網站效能，請使用下列策略來減少產品變異數：

- 在不同產品間分配變異數，以重新建構目錄。
- 移除非庫存的可設定屬性選項。
- 透過自訂選項、類別、相關、分組和捆綁產品等替代功能管理變異。

## 潛在的效能影響

若超過建議的產品變數數，可能會透過下列方式影響網站效能：

- 包含複雜產品的產品詳細資訊和類別頁面的請求和轉譯時間過長。
- 增加回應時間以在管理員中完成儲存作業。
- 增加轉譯「產品編輯」表單的時間。
- 結帳緩慢。

## 其他資訊

- [建立可設定的產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 訓練 — [使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
