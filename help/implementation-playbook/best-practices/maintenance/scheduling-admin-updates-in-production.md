---
title: 正在排程生產網站上的管理員更新
description: 瞭解排程Adobe Commerce重要更新以防止效能緩慢和中斷的最佳實務。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
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
- [私人內容：讓私人內容失效](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [硬體建議：快取](../../../performance/hardware.md#caches)
- [進階設定：設定Redi](../../../performance/advanced-setup.md#set-up-redis)
