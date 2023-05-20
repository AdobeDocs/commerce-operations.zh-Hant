---
title: 產品變體配置最佳實踐
description: 瞭解如何通過限制配置的產品變體數量來優化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 配置產品變體的最佳做法

為獲得最佳效能，請配置每個產品最多50個變體。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 減少產品變更數

為獲得最佳站點效能，請使用以下策略減少產品變體數：

- 通過在不同產品之間分配變體數來重組目錄。
- 刪除非庫存的可配置屬性選項。
- 通過定制選項、類別、相關、分組和捆綁產品等替代功能管理變體。

## 潛在效能影響

超過建議的產品變更數可能會通過以下方式影響站點效能：

- 對包含複雜產品的產品詳細資訊和類別頁面的長請求和呈現時間。
- 在管理員中完成保存操作的響應時間延長。
- 顯示「產品編輯」表單的時間增加。
- 結帳緩慢。

## 其他資訊

- [建立可配置產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 培訓 — [使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
