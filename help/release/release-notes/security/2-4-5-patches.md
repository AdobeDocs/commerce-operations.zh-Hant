---
title: Adobe Commerce 2.4.5安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.5版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---


# Adobe Commerce 2.4.5安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p15

Adobe Commerce 2.4.5-p15安全性版本針對舊版2.4.5中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-94](https://helpx.adobe.com/tw/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>2.4.5的延伸支援安全性修補程式僅供Adobe Commerce客戶使用。 這些修補程式不適用於Magento Open Source程式碼基底。 請參閱[延伸支援](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)。


## 2.4.5-p14

Adobe Commerce 2.4.5-p14安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-71](https://helpx.adobe.com/tw/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.5-p13

Adobe Commerce 2.4.5-p13安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-50](https://helpx.adobe.com/tw/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

* **API效能增強** — 解決先前安全性修補程式之後引入的大量非同步Web API端點效能降低的問題。<!-- AC-14078 -->

* **CMS封鎖存取修正** — 解決具有受限制許可權（例如僅限銷售存取）的管理員使用者無法檢視[!UICONTROL CMS Blocks]清單頁面的問題。

  以前，這些使用者在安裝先前的安全性修補程式後，由於遺失設定引數而發生錯誤。<!-- AC-14087 -->

* **Cookie限制相容性** — 解決框架中涉及`MAX_NUM_COOKIES`常數的回溯不相容變更。 此更新會還原預期行為，並確保與Cookie限制互動的擴充功能或自訂功能的相容性。<!-- AC-14475 -->

* **非同步作業** — 已限制用於覆寫先前客戶訂單的非同步作業。<!-- AC-13917 -->

## 2.4.5-p12

Adobe Commerce 2.4.5-p12安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-26](https://helpx.adobe.com/tw/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-p11

Adobe Commerce 2.4.5-p11安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-08](https://helpx.adobe.com/tw/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

Adobe Commerce 2.4.5-p10安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-73](https://helpx.adobe.com/tw/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5 - p9

Adobe Commerce 2.4.5-p9安全性版本針對2.4.5舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-61](https://helpx.adobe.com/tw/security/products/magento/apsb24-61.html)。

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5 - p8

Adobe Commerce 2.4.5-p8安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-40](https://helpx.adobe.com/tw/security/products/magento/apsb24-40.html)。

### 套用CVE-2024-34102的Hotfix

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 平台升級

* **MariaDB 10.5支援**。 此修補程式發行版本引入與MariaDB 10.5版的相容性。Adobe Commerce仍與MariaDB 10.4版相容，但Adobe建議僅在MariaDB 10.5版中使用Adobe Commerce 2.4.5-p8以及所有即將發行的2.4.5僅限安全性修補程式版本，因為MariaDB 10.4的維護作業將於2024年6月18日結束。<!--AC-11530-->

### 反白顯示

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5 - p7

Adobe Commerce 2.4.5-p7安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-18](https://helpx.adobe.com/tw/security/products/magento/apsb24-18.html)。

## 2.4.5 - p6

Adobe Commerce 2.4.5-p6安全性版本針對2.4.5舊版中已發現的漏洞提供安全性錯誤修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-03](https://helpx.adobe.com/tw/security/products/magento/apsb24-03.html)。

### 反白顯示

此版本引進了兩項重要的安全性增強功能：

* **未產生快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 （未產生的快取金鑰是透過範本指示詞語法或`setCacheKey`或`setData`方法設定的金鑰。）
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。<!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**。 Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商戶可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)來控制這個新限制。<!-- AC-8753 -->

## 2.4.5 - p5

Adobe Commerce 2.4.5-p5安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-50](https://helpx.adobe.com/tw/security/products/magento/apsb23-50.html)。

### 反白顯示

此發行版本引入新的全頁快取組態設定，有助於減輕與`{BASE-URL}/page_cache/block/esi HTTP`端點相關的風險。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;組態設定會設定此端點的`handles`引數值，此引數會決定每個API允許的控點數目上限。 此屬性的預設值為100。 商戶可從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)變更此值。<!-- AC-9113 -->

### 已知問題

**問題**： Adobe Commerce在Composer從&#x200B;**下載期間顯示**&#x200B;錯誤的總和檢查碼`repo.magento.com`錯誤，且封裝下載已中斷。 此問題可能發生於下載發行前期間提供的發行套件期間，而且是由重新封裝`magento/module-page-cache`套件所造成。

**因應措施**：在下載期間看到此錯誤的商家可執行下列步驟：

1) 刪除專案內的`/vendor`目錄（如果存在）。
2) 執行`bin/magento composer update magento/module-page-cache`命令。 這個命令只會更新`page cache`封裝。

如果檢查值問題持續發生，請先移除`composer.lock`檔案，再重新執行`bin/magento composer update`命令以更新每個封裝。

## 2.4.5 - p4

Adobe Commerce 2.4.5-p4安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-42](https://helpx.adobe.com/tw/security/products/magento/apsb23-42.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source 2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[jQuery UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6)知識庫文章所指定的修補程式。

## 2.4.5 - p3

Adobe Commerce 2.4.5-p3安全性版本針對先前版本2.4.5中發現的弱點提供安全性修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告](https://helpx.adobe.com/tw/security/products/magento/apsb23-35.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source 2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[查詢UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6)知識庫文章所指定的修補程式。

### 反白顯示

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點的預設行為已變更。 依預設，API現在一律會傳回`true`。 商家可以啟用原始行為，如果電子郵件不存在於資料庫中，則會傳回`true`；如果存在，則會傳回`false`。<!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **清漆快取7.3支援**。 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7.2.x版本仍維持相容性，但我們建議僅將Adobe Commerce 2.4.5-p3與Varnish Cache 7.3或6.0版LTS搭配使用。

* **RabbitMQ 3.11支援**。 此版本相容於最新版RabbitMQ 3.11。與RabbitMQ 3.9的相容性維持不變（2023年8月之前提供支援），但我們建議僅將Adobe Commerce 2.4.5-p3與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**。 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括`moment.js`程式庫(v2.29.4)、`jQuery UI`程式庫(v1.13.2)和`jQuery`驗證外掛程式程式庫(v1.19.5)。

## 2.4.5 - p2

Adobe Commerce 2.4.5-p2安全性版本針對先前版本2.4.5中發現的漏洞提供三項安全性修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-17](https://helpx.adobe.com/tw/security/products/magento/apsb23-17.html)。

## 2.4.5 - p1

Adobe Commerce 2.4.5-p1安全性版本針對先前版本2.4.5中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB22-48](https://helpx.adobe.com/tw/security/products/magento/apsb22-48.html)。

其中一項安全性錯誤修正包括建立新的組態設定。 如果電子郵件已變更，[!UICONTROL **需要電子郵件確認**]&#x200B;組態設定可讓管理員在管理員使用者變更其電子郵件地址時，需要電子郵件確認。<!-- AC-6292-->

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
