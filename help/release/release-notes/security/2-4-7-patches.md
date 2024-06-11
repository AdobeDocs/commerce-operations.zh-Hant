---
title: Adobe Commerce 2.4.7安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.7版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
source-git-commit: e7557f6eb32bec377f426b6de3bd00ab6cc4113c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Adobe Commerce 2.4.7安全性修補程式的發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Adobe Commerce 2.4.7-p1安全性版本針對2.4.7舊版中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## 安全性反白顯示

此版本包含 [一次性密碼(OTP)設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) 讓Google Authenticator解決 [向後不相容的變更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 在2.4.7中。「 」的說明 **[!UICONTROL OTP Window]** 欄位現在會提供設定的精確說明，而且預設值已從 `1` 至 `29`.

## 此版本中包含的Hotfix

Adobe Commerce 2.4.7-p1解決了UPS整合從SOAP移轉至REST API的範圍中發生的問題。 此問題會影響出貨到美國境外的客戶，使他們無法使用公制系統/SI測量方式（千克與公分）來建立搭配UPS的出貨。 請參閱 [UPS送貨方法整合從SOAP移轉至RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) 知識庫文章以取得詳細資訊。
