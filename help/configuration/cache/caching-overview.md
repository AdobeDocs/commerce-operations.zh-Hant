---
title: 配置快取
description: 瞭解快取以及如何為Adobe Commerce和Magento Open Source應用程式配置快取機制。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 配置快取

[!DNL Commerce] 允許您配置預設檔案系統快取的替代選項。 本指南討論了其中的一些備選方案；即

- 在 [!DNL Commerce] 配置：

   - [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [雷迪斯](config-redis.md)
   - 檔案系統（預設）:使用預設檔案系統快取不需要配置。

- 設定 [清漆](config-varnish.md) 不修改 [!DNL Commerce] 配置。

## 快取術語

[!DNL Commerce] 使用以下快取術語：

- **額** — 類似於快取儲存的介面或網關，由 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)。
- **快取類型** — 可以是提供的類型之一 [!DNL Commerce] 或者 [建立自己的](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)。
- **後端** — 指定有關 [快取儲存](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，由 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **兩級後端** — 將快取記錄儲存在兩個後端：一個更快，一個更慢。

   >[!INFO]
   >
   >二級後端快取配置超出本指南的範圍。

## 配置選項

- 修改提供的 `default` 快取前端 — 

   您僅修改 `<magento_root>/app/etc/di.xml` 檔案，即Commerce應用程式的全局依賴項注入配置。

- 配置您自己的自定義快取前端 — 

   您僅修改 `<magento_root>/app/etc/env.php` 檔案，因為它會覆蓋 `di.xml` 的子菜單。

>[!TIP]
>
>清漆不要求更改 [!DNL Commerce] 配置。 請參閱 [配置和使用清漆](config-varnish.md)。
