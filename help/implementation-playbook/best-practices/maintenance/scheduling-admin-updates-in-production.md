---
title: 計畫生產站點上的管理更新
description: 瞭解將關鍵更新安排到Adobe Commerce以防止效能下降和停機的最佳做法。
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 在生產站點上安排管理更新的最佳做法

安排在非高峰時段在您的Adobe Commerce站點上進行關鍵更新和操作，以防止生產站點上效能下降和停機。

關鍵操作示例：

- 管理員配置更改，例如更新產品屬性或將產品子類別移動到其他類別
- 資料導入或導出操作

關鍵操作會導致快取失效和重新索引操作，這會顯著增加可能導致站點停機的響應時間。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 其他資訊

- [快取的最佳做法](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [專用內容：使私有內容無效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬體建議：快取](../../../performance/hardware.md#caches)
- [高級設定：設定Redis](../../../performance/advanced-setup.md#set-up-redis)
