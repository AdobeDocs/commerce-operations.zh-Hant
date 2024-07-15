---
title: 防止快取中毒
description: 瞭解如何防止Commerce店面的頁面快取中毒。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 防止快取中毒

本主題說明使用Microsoft Internet Information Server (IIS)網頁伺服器時，如何防止快取中毒。 _快取中毒_&#x200B;是一種將快取內容變更為包含相同網站不同頁面的方法。 例如，可以插入HTTP 404 （找不到）錯誤頁面來取代某些良性頁面（例如店面首頁），這可能會導致潛在的拒絕服務(DoS)。 Varnish或Redis已快取惡意頁面URL，因此名稱為&#x200B;_頁面快取中毒_。

這些型別的攻擊可能很難偵測，因為它們不會導致網頁伺服器記錄發生錯誤。

此解決方案適用於下列Commerce版本：

- 2.0.10和更新版本
- 2.1.2和更新版本

>[!INFO]
>
>本主題適用於有經驗的IIS管理員。

## 說明

如果IIS伺服器上啟用了URL重寫，並且在請求到達Varnish或Redis快取服務之前變更了以下任何HTTP標頭，則會導致此問題：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果變更這些標頭，則會快取產生的URL和內容，導致潛在的漏洞。

## 解決方案

我們提供根據`Enable_IIS_Rewrites`的IIS伺服器設定，移除所有先前標題的值的選項。

- 如果`Enable_IIS_Rewrites`設定為`0`，則會移除標頭的值。
- 如果`Enable_IIS_Rewrites`設定為`1`，則標頭的值將保持不變。

>[!WARNING]
>
>如果您將`Enable_IIS_Rewrites`設為`1`，則在要求傳至IIS網頁伺服器之前，您不得允許變更前述標頭的值。
