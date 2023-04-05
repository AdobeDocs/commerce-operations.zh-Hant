---
title: 配置快取
description: 了解快取以及如何設定Adobe Commerce和Magento Open Source應用程式的快取機制。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 配置快取

[!DNL Commerce] 可讓您設定預設檔案系統快取的替代選項。 本指南討論了其中一些備選方案；即

- 在 [!DNL Commerce] 配置：

   - [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [雷迪斯](config-redis.md)
   - 檔案系統（預設）:使用預設檔案系統快取無需配置。

- 設定 [清漆](config-varnish.md) 不修改 [!DNL Commerce] 設定。

## 快取術語

[!DNL Commerce] 使用下列快取術語：

- **前端** — 類似於快取儲存的介面或網關，由 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **快取類型** — 可以是 [!DNL Commerce] 或者 [建立自己的](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **後端** — 指定有關的詳細資訊 [快取儲存](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，實作於 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **二級後端** — 將快取記錄儲存在兩個後端：更快，慢。

   >[!INFO]
   >
   >兩級後端快取配置不在本指南中。

## 配置選項

- 修改提供的 `default` 快取前端 — 

   您僅修改 `<magento_root>/app/etc/di.xml` 檔案，即商務應用程式的全域相依性插入設定。

- 配置自定義快取前端 — 

   您僅修改 `<magento_root>/app/etc/env.php` 檔案，因為它會覆寫 `di.xml` 檔案。

>[!TIP]
>
>清漆不需要變更 [!DNL Commerce] 設定。 請參閱 [配置和使用清漆](config-varnish.md).
