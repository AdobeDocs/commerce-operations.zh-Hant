---
title: 設定網站、存放區和存放區檢視的最佳作法
description: 瞭解設定網站、商店和商店檢視的最佳實務，以最大化網站效能。
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 設定網站、商店和商店檢視的最佳實務

針對雲端基礎結構上的Adobe Commerce，最佳實務尤其適用於生產環境（並可能適用於專業架構上的測試，受資源限制），其擁有的資源會多於整合和開發環境。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 提升效能的策略

如果您的專案需要許多網站、商店或商店檢視，您可以使用以下策略來提高效能：

- 將邏輯切換到類別來重新建構目錄
- 使用外部價格與「價格管理系統(PMS)」，將價目表與型錄資料分開。
- 使用替代noSQL資料儲存體，例如Elasticsearch

## 對效能的潛在影響

網站和商店是目錄資料的倍數，因此擁有許多網站和商店可能會對網站效能產生下列負面影響：

- 較大的索引表格會增加完成索引作業[價格索引]所需的時間。
- 擷取應用程式設定的時間增加，會降低非快取目錄頁面的店面回應時間。
- 由於會針對每個網站個別儲存資料，因此在「管理員」中完成「儲存」作業所需的時間會大幅增加。


## 其他資訊

- [瞭解網站、商店和商店檢視](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [設定多個網站或商店](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
