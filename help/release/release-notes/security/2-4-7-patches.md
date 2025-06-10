---
title: Adobe Commerce 2.4.7安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.7版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 11044555f0e661fcbdbb5e6a41b9790ca244f31a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Adobe Commerce 2.4.7安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7 - p6

Adobe Commerce 2.4.7-p6安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

* **MariaDB支援** — 新增對MariaDB 10.11的支援。

* **API效能增強** — 解決先前安全性修補程式之後引入的大量非同步Web API端點效能降低的問題。<!-- AC-14078 -->

* **CMS封鎖存取修正** — 解決具有受限制許可權（例如僅限銷售存取）的管理員使用者無法檢視[!UICONTROL CMS Blocks]清單頁面的問題。

  以前，這些使用者在安裝先前的安全性修補程式後，由於遺失設定引數而發生錯誤。<!-- AC-14087 -->

* **Cookie限制相容性** — 解決框架中涉及`MAX_NUM_COOKIES`常數的回溯不相容變更。 此更新會還原預期行為，並確保與Cookie限制互動的擴充功能或自訂功能的相容性。<!-- AC-14475 -->

* **CVE-2024-34104**&#x200B;的修正 — 解決不適當的授權漏洞。<!-- AC-13917 -->

* **修正CVE-2025-47110** — 解決電子郵件範本的弱點。<!-- AC-14695 -->

>[!BEGINSHADEBOX]

CVE-2025-47110的修正也以隔離修補程式的形式提供。 如需詳細資訊，請參閱[知識庫文章](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

## 2.4.7 - p5

Adobe Commerce 2.4.7-p5安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

此發行版本也引入對Adobe Commerce [HIPAA就緒擴充功能](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)的支援。

>[!ENDSHADEBOX]

### 已知問題

**問題**：安裝PHP 8.2或更新版本的2.4.7-p5時，系統會安裝2.4.8或更新版本的`paypal/module-braintree` 4.7.0版。 對於PHP 8.1，使用正確的Braintree版本4.6.1-p5。 這個不符是由於Metapackage中對`adobe-commerce/extensions-metapackage: ~2.0`的鬆散相依性所造成。 這會影響PHP 8.2+部署的相容性和支援的功能集。<!-- ACPLTSRV-6276) -->

此外，針對2.4.7-p3、2.4.7-p4和2.4.7-p5版，可能會安裝Braintree擴充功能4.6.1-p5版，而部分使用者則預期4.6.1-p3或p4版，因為先前較嚴格的相依性已放鬆，而允許在發行版本線內進行擴充功能升級。<!-- AC-14430 -->

**因應措施**：若要確保您的PHP版本有正確的Braintree版本，請執行`composer update`安裝由`adobe-commerce/extensions-metapackage:2.0.0`相依性指定的適當版本。

## 2.4.7 - p4

Adobe Commerce 2.4.7-p4安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7 - p3

Adobe Commerce 2.4.7-p3安全性版本針對2.4.7舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的Hotfix

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

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 套用CVE-2024-34102的Hotfix

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 反白顯示

此版本包含下列重點專案：

* **更新Google Authenticator的[一次性密碼(OTP)設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** — 需要此更新來解決2.4.7中[回溯不相容變更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)所導致的錯誤。**[!UICONTROL OTP Window]**&#x200B;欄位的描述現在提供設定的正確說明，預設值已從`1`變更為`29`。

* **B2B版本相容性** — 為了與Commerce 2.4.7-p1版相容，擁有Adobe Commerce B2B擴充功能的商家必須升級至[B2B 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)版。

### 此版本中包含的Hotfix

Adobe Commerce 2.4.7-p1解決了UPS整合從SOAP移轉至REST API的範圍中發生的問題。 此問題會影響出貨到美國境外的客戶，使他們無法使用公制系統/SI測量方式（千克與公分）來建立搭配UPS的出貨。 請參閱[UPS送貨方法整合從SOAP移轉至RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)知識庫文章以取得詳細資料。
