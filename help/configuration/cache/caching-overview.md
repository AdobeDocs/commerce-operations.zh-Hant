---
title: 設定快取
description: 瞭解快取以及如何設定Adobe Commerce應用程式的快取機制。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 設定快取

[!DNL Commerce]可讓您設定預設檔案系統快取的替代方案。 本指南會說明其中部分替代方案，即

- 在[!DNL Commerce]設定中設定下列快取機制：

   - [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - 檔案系統（預設）：使用預設檔案系統快取不需要任何設定。

- 設定[清漆](config-varnish.md)而不修改[!DNL Commerce]組態。

## 快取術語

[!DNL Commerce]使用下列快取術語：

- **Frontend** — 類似快取儲存的介面或閘道，由[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)實作。
- **快取型別** — 可以是[!DNL Commerce]提供的型別之一，或者您可以[建立自己的型別](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)。
- **後端** — 指定有關[快取存放區](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)的詳細資料，由[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)實作
- **雙層後端** — 將快取記錄儲存在兩個後端：快一個與慢一個後端。

  >[!INFO]
  >
  >雙層後端快取設定不在本指南的涵蓋範圍內。

## 設定選項

- 正在修改提供的`default`快取前端 — 

  您只會修改`<magento_root>/app/etc/di.xml`檔案(Commerce應用程式的全域相依性插入組態)。

- 設定您自己的自訂快取前端 — 

  您只修改`<magento_root>/app/etc/env.php`檔案，因為它覆寫`di.xml`檔案中的對應組態。

>[!TIP]
>
>塗漆不需要變更[!DNL Commerce]設定。 請參閱[設定及使用清漆](config-varnish.md)。
