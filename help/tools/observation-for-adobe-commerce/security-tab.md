---
title: 的 [!UICONTROL Security] 頁籤
description: 瞭解 [!UICONTROL Security] 頁籤 [!DNL Observation for Adobe Commerce]。
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 的 [!UICONTROL Security] 頁籤

的 **[!UICONTROL Security]** 頁籤解釋安全問題並隔離其潛在原因。 此外，還描述了頁籤的框架。

## [!UICONTROL API calls by IP, details by URL]

的 **[!UICONTROL API calls by IP, details by URL]** frame顯示選定時間範圍內按IP進行的API調用數。 此幀顯示該IP地址訪問的IP地址和API URL。

![按IP調用API](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

的 **[!UICONTROL Forgot Password]** 訪問框架顯示選定時間範圍內忘記密碼嘗試的次數。 針對IP地址的高活動可能是站點上的攻擊。

![忘記密碼](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

的 **[!UICONTROL Create Account access]** frame顯示選定時間範圍內新帳戶活動的數量。 來自單個IP地址的高活動可能指示攻擊。

![建立帳戶訪問](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

的 **[!UICONTROL POST activities]** 框顯示 `POST` 站點活動，分面 `client_ip` 從 [!DNL Fastly] 日誌。 它還顯示IP地址訪問的URL。

![POST活動](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

的 **[!UICONTROL POST activities summary table]** 框顯示摘要 `POST` 站點活動，分面 `client_ip` 從 [!DNL Fastly] 日誌。 它還顯示IP地址訪問的URL的計數。 該計數是所選時段的。

![POST活動摘要](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

的 **[!UICONTROL POST activities details table]** 框顯示 `POST` 站點的活動 [!DNL Fastly] 日誌。 它還顯示 [!DNL Fastly] 記錄這些請求。 僅限於最近2000項請求。
![POST活動詳細資訊](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

的 **[!UICONTROL Guest Carts activities]** frame顯示選定時段內按IP地址和訪問的URL分面的來賓購物車活動數。 客推車可用於梳理攻擊。 此框架顯示訪問來賓操作站URL的請求總數。

![客車活動](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

的 **[!UICONTROL API – forgot password, create account by Countries]** frame顯示在選定時間範圍內建立的帳戶數和重置忘記密碼的請求數。 還應多方面顯示請求的來源國。 這一框架側重於請求的原產國。

![api-forgot國家](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

的 **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame顯示在選定時間範圍內建立的帳戶數和重置忘記密碼的請求數。 還可以分面顯示請求的IP地址、訪問的URL和原始國家（地區）。 此幀側重於IP的計數。

![api forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

的 **[!UICONTROL Guest cart activities by IP]** frame按IP顯示所選時段的來賓購物車活動。

![來賓操作站IP](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

的 **[!UICONTROL Guest cart activities by Countries]** frame顯示所選時段內各國家/地區的來賓購物車活動。

![客車鄉](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
