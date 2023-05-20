---
title: 配置站點、商店和商店視圖的最佳做法
description: 瞭解配置站點、儲存和儲存視圖以最大化站點效能的最佳做法。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 配置站點、商店和商店視圖的最佳做法

為獲得最佳站點效能，請為Adobe Commerce配置最多50個站點、50個商店和50個商店視圖，用於雲基礎架構項目。

>[!NOTE]
>
>對於Adobe Commerce雲基礎架構，最佳做法具體適用於生產環境（可能適用於Pro體系結構上的暫存，但受資源限制），這些環境的資源將比整合和開發環境更多。 對於整合（Pro和Starter）和暫存環境(Starter)，將儲存視圖數量減少到5或10個以下（需經技術審查）。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 提高績效的策略

如果您的項目需要許多站點、商店或商店視圖，則可以使用以下策略來提高效能：

- 通過將邏輯轉換到類別來重構目錄
- 使用外部價格和價格管理系統(PMS)將價目表與目錄資料分離。
- 使用備選的noSQL資料儲存，如Elasticsearch

## 潛在的效能影響

網站和商店是目錄資料的乘數，因此，擁有許多網站和商店可能會通過以下方式對站點效能產生負面影響：

- 較大的索引表增加了完成索引操作所需的時間 [價格指數]。
- 檢索應用程式配置的時間增加會縮短非快取目錄頁的儲存前響應時間。
- 由於在每個網站中單獨保存資料，因此在管理員中完成保存操作所需的時間顯著增加。


## 其他資訊

- [瞭解網站、商店和商店視圖](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
