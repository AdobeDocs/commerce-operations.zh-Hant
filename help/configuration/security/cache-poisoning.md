---
title: 防止快取中毒
description: 瞭解如何防止您的Commerce商店的頁面快取中毒。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# 防止快取中毒

本主題討論如何防止 [快取](https://glossary.magento.com/cache) 使用MicrosoftInternet Information Server(IIS)Web伺服器時中毒。 _快取中毒_ 是一種將快取內容更改為包含來自同一站點的不同頁面的方法。 例如，可以插入HTTP 404（未找到）錯誤頁來代替某些良性頁(例如， [店面](https://glossary.magento.com/storefront) 首頁)，這可能導致潛在的拒絕服務(DoS)。 惡意頁面URL由清漆或Redis快取，因此名稱 _頁面快取中毒_。

這些類型的攻擊可能難以檢測，因為它們不會導致Web伺服器日誌中的錯誤。

此解決方案適用於以下Commerce版本：

- 2.0.10和更高版本
- 2.1.2和更高版本

>[!INFO]
>
>本主題針對經驗豐富的IIS管理員。

## 說明

如果在IIS伺服器上啟用了URL重寫，並且在請求到達清漆或Redis快取服務之前更改了以下任何HTTP標頭，則會導致問題：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果更改了這些標頭，則會快取生成的URL和內容，從而導致潛在的漏洞。

## 解決方案

我們提供了一個選項，用於根據IIS伺服器設定刪除前面所有標頭的值 `Enable_IIS_Rewrites`。

- 如果 `Enable_IIS_Rewrites` 設定為 `0`，將刪除標題的值。
- 如果 `Enable_IIS_Rewrites` 設定為 `1`，標題的值將保持不變。

>[!WARNING]
>
>如果設定 `Enable_IIS_Rewrites` 至 `1`，在請求到達IIS Web伺服器之前，不能更改前面標頭的值。
