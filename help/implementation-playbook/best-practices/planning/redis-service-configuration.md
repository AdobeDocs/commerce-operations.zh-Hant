---
title: Redis服務配置的最佳做法
description: 了解如何使用Adobe Commerce 2.3.5的延伸Redis快取實作，以改善快取效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Redis服務配置的最佳做法

- 若是部署在雲端基礎架構上的Adobe Commerce 2.3.3及更新版本，請升級至Redis 5.0版。
- 若為Adobe Commerce 2.3.5版或更新版本，請使用延伸Redis快取實作。 此實作包含下列最佳化措施，以將對來自Adobe Commerce的每個請求執行的Redis查詢數減到最少：
   - 縮小Redis和Adobe Commerce之間的網路資料傳輸大小
   - 通過提高適配器自動確定需要載入的內容的能力，降低CPU週期的Redis消耗
   - 減少Redis寫操作上的競爭條件

## 受影響的產品和版本

Adobe Commerce，使用2.3.3版或更新版本的雲端基礎架構。
Adobe Commerce（所有部署方法）、2.3.5版和更新版本

## 更新雲端部署的Redis版本

若是使用Adobe Commerce 2.3.3或更新版本在雲端基礎架構上部署Adobe Commerce，請將Redis服務升級至Redis 5.0版。如需指示，請參閱Adobe Commerce中有關雲端基礎架構檔案的下列主題：

- [設定Redis服務](https://devdocs.magento.com/cloud/project/services-redis.html)
- [更改服務版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## 配置擴展的Redis快取實施

若為Adobe Commerce 2.3.5及更新版本，請更新您的設定以使用延伸Redis快取實作 `\Magento\Framework\Cache\Backend\Redis`.

### 雲端部署的設定

使用 `ece-tools` 2002.1.1或更新版本，請設定 `REDIS_BACKEND` 部署變數， `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

如需詳細資訊，請參閱 [部署變數> `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) 在有關雲端基礎架構的Adobe Commerce檔案中。

>[!NOTE]
>
> 從命令列使用，檢查您本機雲端環境中安裝的ece-tools版本 `composer show magento/ece-tools` 命令。 如有必要， [更新ece-tools版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

### 內部部署的配置

對於Adobe Commerce內部部署，請使用 `bin/magento:setup` 命令。 如需指示，請參閱 [預設快取使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 其他資訊

- [Adobe Commerce版本2.3.5 — 效能提升](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [密頁快取](../../../configuration/cache/redis-pg-cache.md)


