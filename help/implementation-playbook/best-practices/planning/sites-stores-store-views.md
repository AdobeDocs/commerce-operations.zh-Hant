---
title: 設定網站、商店和商店檢視的最佳作法
description: 了解設定網站、商店和商店檢視的最佳實務，以發揮網站效能的最大效益。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 設定網站、商店和商店檢視的最佳作法

為獲得最佳網站效能，請在雲端基礎架構專案上為Adobe Commerce設定最多50個網站、50個商店和50個商店檢視。

>[!NOTE]
>
>針對雲端基礎架構上的Adobe Commerce，最佳實務特別適用於生產環境（可能適用於Pro架構上的預備，但須受資源限制），其資源會比整合和開發環境更多。 對於整合（Pro和Starter）和測試環境(Starter)，將商店檢視次數減少至5或10次以下（經技術審核）。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 提高效能的策略

如果您的專案需要許多網站、商店或商店檢視，您可以使用下列策略來改善效能：

- 通過將邏輯轉換為類別來重構目錄
- 使用外部價格和價格管理系統(PMS)將價目表與目錄資料分開。
- 使用替代的noSQL資料儲存，如Elasticsearch

## 潛在績效影響

網站和存放區是目錄資料的乘數，因此擁有許多網站和存放區可能會透過下列方式對網站效能造成負面影響：

- 較大的索引表增加了完成索引操作所需的時間 [價格指數].
- 擷取應用程式設定的時間增加，會降低非快取目錄頁面的店面回應時間。
- 管理員中完成儲存作業所需的時間大幅增加，因為資料會分別儲存至每個網站。


## 其他資訊

- [了解網站、商店和商店的檢視](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

