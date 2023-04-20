---
title: 「 [!UICONTROL Security] 標籤」
description: 了解 [!UICONTROL Security] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 5e4ab9e62f395b0967c3a632659c70a22770e9db
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 此 [!UICONTROL Security] 標籤

此 **[!UICONTROL Security]** tab說明安全性問題，並隔離其潛在原因。 此外，還描述了頁簽的框架。

## [!UICONTROL API calls by IP, details by URL]

此 **[!UICONTROL API calls by IP, details by URL]** frame會依IP在選取的時間範圍內顯示API呼叫數。 此框架顯示該IP地址訪問的IP地址和API URL。

![依IP的API呼叫](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

此 **[!UICONTROL Forgot Password]** 訪問框架顯示選定時間範圍內忘記密碼嘗試的次數。 針對IP位址的高活動可能是網站上的攻擊。

![忘記密碼](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

此 **[!UICONTROL Create Account access]** 框架顯示在選定時間範圍內的新帳戶活動數。 來自單個IP地址的高活動可能表示攻擊。

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

此 **[!UICONTROL POST activities]** 框顯示 `POST` 網站活動，分面 `client_ip` 從 [!DNL Fastly] 記錄檔。 也會顯示IP位址所存取的URL。

![POST活動](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

此 **[!UICONTROL POST activities summary table]** 框顯示摘要 `POST` 網站活動，分面 `client_ip` 從 [!DNL Fastly] 記錄檔。 它也會顯示IP位址所存取之URL的計數。 計數是針對所選時間範圍。

![POST — 活動 — 摘要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

此 **[!UICONTROL POST activities details table]** 框顯示 `POST` 網站的活動 [!DNL Fastly] 記錄檔。 它也會顯示 [!DNL Fastly] 記錄這些請求。 僅限於最近2000個請求。
![POST — 活動 — 詳細資料](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

此 **[!UICONTROL Guest Carts activities]** frame會顯示在選取的時間範圍內（依存取的IP位址和URL分段）的來賓購物車活動數量。 來賓購物車可用於梳理攻擊。 此框架顯示訪客購物車URL被存取的請求總數。

![來賓 — 購物車活動](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

此 **[!UICONTROL API – forgot password, create account by Countries]** frame會顯示在選取的時間範圍內建立的帳戶數，以及重設忘記密碼的要求數。 此外，還應多方面顯示請求的來源國。 這一框架側重於請求的來源國。

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

此 **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame會顯示在選取的時間範圍內建立的帳戶數，以及重設忘記密碼的要求數。 此範本可多面顯示請求的IP位址、已存取的URL，以及來源國。 此框架的重點是IP的計數。

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

此 **[!UICONTROL Guest cart activities by IP]** 框架會依IP在選取的時間範圍內顯示來賓購物車活動。

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

此 **[!UICONTROL Guest cart activities by Countries]** frame會依所選時間範圍內的國家/地區顯示訪客購物車活動。

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
