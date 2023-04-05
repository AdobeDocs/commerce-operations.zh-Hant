---
title: 防止快取中毒
description: 了解如何為您的Commerce店面防止頁面快取中毒。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 防止快取中毒

本主題討論如何在使用Microsoft Internet Information Server(IIS)Web伺服器時防止快取中毒。 _快取中毒_ 是一種將快取內容變更為包含來自相同網站之不同頁面的方法。 例如，可以插入HTTP 404（找不到）錯誤頁面來取代某些良性頁面（例如，店面首頁），這可能導致拒絕服務(DoS)。 惡意頁面URL由清漆或紅色快取，因此名稱 _頁面快取中毒_.

這些類型的攻擊可能難以檢測，因為它們不會導致Web伺服器日誌中的錯誤。

此解決方案適用於下列商務版本：

- 2.0.10及更新版本
- 2.1.2和更新版本

>[!INFO]
>
>本主題針對經驗豐富的IIS管理員。

## 說明

如果在IIS伺服器上啟用了URL重寫，並且在請求到達清漆或紅色快取服務之前更改了以下任何HTTP標頭，則會導致此問題：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果變更這些標題，系統會快取產生的URL和內容，進而產生潛在漏洞。

## 解決方案

我們提供了基於的IIS伺服器設定刪除前面所有標題的值的選項 `Enable_IIS_Rewrites`.

- 若 `Enable_IIS_Rewrites` 設為 `0`，則會移除標題的值。
- 若 `Enable_IIS_Rewrites` 設為 `1`，標題的值將保持不變。

>[!WARNING]
>
>如果您設定 `Enable_IIS_Rewrites` to `1`，則不得在請求到達IIS web伺服器之前更改前面標題的值。
