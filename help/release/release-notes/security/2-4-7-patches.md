---
title: Adobe Commerce 2.4.7安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.7版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Adobe Commerce 2.4.7安全性修補程式的發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Adobe Commerce 2.4.7-p1安全性版本針對2.4.7舊版中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## 安全性反白顯示

此版本包含 [一次性密碼(OTP)設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) 讓Google Authenticator解決 [向後不相容的變更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 在2.4.7中。「 」的說明 **[!UICONTROL OTP Window]** 欄位現在會提供設定的精確說明，而且預設值已從 `1` 至 `29`.
