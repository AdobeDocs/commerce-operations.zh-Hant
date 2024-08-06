---
title: Adobe Commerce 2.4.5安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.5版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 6c8d686fd3a7ce76f966b9f390813f454aa093bf
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 0%

---


# Adobe Commerce 2.4.5安全性修補程式的發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

Adobe Commerce 2.4.5-p8安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 套用CVE-2024-34102的Hotfix

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### 平台升級

* **MariaDB 10.5支援**。 此修補程式發行版本引入與MariaDB 10.5版的相容性。Adobe Commerce仍與MariaDB 10.4版相容，但Adobe建議使用Adobe Commerce 2.4.5-p8以及所有即將發行的2.4.5僅限安全性修補程式版本，僅與MariaDB 10.5版相容，因為MariaDB 10.4維護作業將於2024年6月18日結束。<!--AC-11530-->

### 其他安全性增強功能

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

Adobe Commerce 2.4.5-p7安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)。

## Adobe Commerce 2.4.5-p6

Adobe Commerce 2.4.5-p6安全性版本針對2.4.5舊版中已發現的漏洞提供安全性錯誤修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)。

### 安全性重點專案

此版本引進了兩項重要的安全性增強功能：

* **未產生快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 （未產生的快取金鑰是透過範本指示詞語法或`setCacheKey`或`setData`方法設定的金鑰。）
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。<!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**。 Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商戶可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)來控制這個新限制。<!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Adobe Commerce 2.4.5-p5安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)。

### 安全性反白顯示

此發行版本引入新的全頁快取組態設定，有助於減輕與`{BASE-URL}/page_cache/block/esi HTTP`端點相關的風險。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;組態設定會設定此端點的`handles`引數值，此引數會決定每個API允許的控點數目上限。 此屬性的預設值為100。 商戶可從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)變更此值。<!-- AC-9113 -->

### 已知問題

**問題**： Adobe Commerce在Composer從`repo.magento.com`下載期間顯示&#x200B;**錯誤的總和檢查碼**&#x200B;錯誤，且封裝下載已中斷。 此問題可能發生於下載發行前期間提供的發行套件期間，而且是由重新封裝`magento/module-page-cache`套件所造成。

**因應措施**：在下載期間看到此錯誤的商家可執行下列步驟：

1) 刪除專案內的`/vendor`目錄（如果存在）。
2) 執行`bin/magento composer update magento/module-page-cache`命令。 這個命令只會更新`page cache`封裝。

如果檢查值問題持續發生，請先移除`composer.lock`檔案，再重新執行`bin/magento composer update`命令以更新每個封裝。

## Adobe Commerce 2.4.5-p4

Adobe Commerce 2.4.5-p4安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)。

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[jQuery UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6)知識庫文章所指定的修補程式。

## Adobe Commerce 2.4.5-p3

Adobe Commerce 2.4.5-p3安全性版本針對先前版本2.4.5中發現的弱點提供安全性修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告](https://helpx.adobe.com/security/products/magento/apsb23-35.html)。

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[查詢UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6)知識庫文章所指定的修補程式。

### 安全性反白顯示

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點的預設行為已變更。 依預設，API現在一律會傳回`true`。 商家可以啟用原始行為，如果電子郵件不存在於資料庫中，則會傳回`true`；如果存在，則會傳回`false`。<!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **清漆快取7.3支援**。 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7.2.x版本仍維持相容性，但我們建議僅將Adobe Commerce 2.4.5-p3與Varnish Cache 7.3或6.0版LTS搭配使用。

* **RabbitMQ 3.11支援**。 此版本與最新版RabbitMQ 3.11相容。RabbitMQ 3.9仍支援相容性至2023年8月，但我們建議僅將Adobe Commerce 2.4.5-p3與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**。 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括`moment.js`程式庫(v2.29.4)、`jQuery UI`程式庫(v1.13.2)和`jQuery`驗證外掛程式程式庫(v1.19.5)。

## Adobe Commerce 2.4.5-p2發行說明

Adobe Commerce 2.4.5-p2安全性版本針對先前版本2.4.5中發現的漏洞提供三項安全性修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html)。

## Adobe Commerce 2.4.5-p1

Adobe Commerce 2.4.5-p1安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html)。

其中一項安全性錯誤修正包括建立新的組態設定。 如果電子郵件已變更，**需要電子郵件確認**&#x200B;組態設定可讓管理員在管理員使用者變更其電子郵件地址時，需要電子郵件確認。<!-- AC-6292-->
