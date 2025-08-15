---
title: 正在排程生產網站上的管理員更新
description: 瞭解排程Adobe Commerce重要更新以防止效能緩慢和中斷的最佳實務。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# 在生產網站上排程管理員更新的最佳實務

在非尖峰時間排程Adobe Commerce網站上的關鍵更新和操作，以防止生產網站上的效能緩慢和中斷。

關鍵動作範例：

- 管理員設定變更，例如更新產品屬性，或將產品子類別移至另一個類別
- 資料匯入或匯出作業

關鍵動作會導致快取失效和重新索引操作，大幅增加回應時間，進而可能導致網站中斷。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 其他資訊

- [快取的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [私人內容：使私人內容無效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬體建議：快取](../../../performance/hardware.md#caches)
- [進階設定：設定Redi](../../../performance/advanced-setup.md#set-up-redis)
