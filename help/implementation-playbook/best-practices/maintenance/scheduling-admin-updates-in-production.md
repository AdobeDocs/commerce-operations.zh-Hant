---
title: 在生產網站上排程管理員更新
description: 了解將重要更新排程至Adobe Commerce以防止效能緩慢和中斷的最佳實務。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 在生產網站上排程管理員更新的最佳實務

在非尖峰時段排程Adobe Commerce網站的重要更新和作業，以防止生產網站的效能緩慢和中斷。

重要動作的範例：

- 管理配置變更，例如更新產品屬性或將產品子類別移至其他類別
- 資料匯入或匯出操作

關鍵操作會導致快取失效和重新索引操作，從而顯著增加可能導致站點中斷的響應時間。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 其他資訊

- [快取最佳作法](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [私人內容：使私人內容無效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬體建議：快取](../../../performance/hardware.md#caches)
- [高級設定：設定Redis](../../../performance/advanced-setup.md#set-up-redis)

