---
title: Adobe Commerce 2.4.7安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.7版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Adobe Commerce 2.4.7安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7 - p5

Adobe Systems Commerce 2.4.7-p5 安全版本為先前版本 2.4.7 中發現的漏洞提供了安全錯誤修復。

有關安全 bug 修補程式的最新資訊，請參閱 [Adobe Systems安全公告 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 反白顯示

此發行版本引入對Adobe Commerce [HIPAA就緒擴充功能](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)的支援。

## 2.4.7 - p4

Adobe Commerce 2.4.7-p4安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7 - p3

Adobe Commerce 2.4.7-p3安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

有關安全 bug 修補程式的最新資訊，請參閱 [Adobe Systems安全公告 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的修補程式

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7 - p2

Adobe Commerce 2.4.7-p2安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7 - p1

Adobe Commerce 2.4.7-p1安全性版本針對2.4.7舊版中發現的弱點提供安全性錯誤修正。

有關安全 bug 修補程式的最新資訊，請參閱 [Adobe Systems安全公告 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### CVE-2024-34102 的套用修補程式

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 反白顯示

此版本包括以下亮點：

* **更新Google Authenticator的[一次性密碼(OTP)設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** — 需要此更新來解決2.4.7中[回溯不相容變更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)所導致的錯誤。**[!UICONTROL OTP Window]**&#x200B;欄位的描述現在提供設定的正確說明，預設值已從`1`變更為`29`。

* **B2B版本相容性** — 為了與Commerce 2.4.7-p1版相容，擁有Adobe Commerce B2B擴充功能的商家必須升級至[B2B 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)版。

### 此版本中包含的Hotfix

Adobe Commerce 2.4.7-p1解決了UPS整合從SOAP移轉至REST API的範圍中發生的問題。 此問題會影響出貨到美國境外的客戶，使他們無法使用公制系統/SI測量方式（千克與公分）來建立搭配UPS的出貨。 請參閱[UPS送貨方法整合從SOAP移轉至RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)知識庫文章以取得詳細資料。
