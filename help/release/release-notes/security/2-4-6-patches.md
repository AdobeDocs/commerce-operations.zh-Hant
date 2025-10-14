---
title: Adobe Commerce 2.4.6安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.6版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: ba5b422f40803e6c5e797e939dd2fc9e3e7c195a
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 0%

---


# Adobe Commerce 2.4.6安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p13

Adobe Commerce 2.4.6-p13安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

## 2.4.6-p12

Adobe Commerce 2.4.6-p12安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.6-p11

Adobe Commerce 2.4.6-p11安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

* **MariaDB支援** — 新增對MariaDB 10.11的支援。

* **API效能增強** — 解決先前安全性修補程式之後引入的大量非同步Web API端點效能降低的問題。<!-- AC-14078 -->

* **CMS封鎖存取修正** — 解決具有受限制許可權（例如僅限銷售存取）的管理員使用者無法檢視[!UICONTROL CMS Blocks]清單頁面的問題。

  以前，這些使用者在安裝先前的安全性修補程式後，由於遺失設定引數而發生錯誤。<!-- AC-14087 -->

* **Cookie限制相容性** — 解決框架中涉及`MAX_NUM_COOKIES`常數的回溯不相容變更。 此更新會還原預期行為，並確保與Cookie限制互動的擴充功能或自訂功能的相容性。<!-- AC-14475 -->

* **非同步作業** — 已限制用於覆寫先前客戶訂單的非同步作業。<!-- AC-13917 -->

## 2.4.6-p10

Adobe Commerce 2.4.6-p10安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6 - p9

Adobe Commerce 2.4.6-p9安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6 - p8

Adobe Commerce 2.4.6-p8安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6 - p7

Adobe Commerce 2.4.6-p7安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 反白顯示

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6 - p6

Adobe Commerce 2.4.6-p6安全性版本針對2.4.6舊版中已發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

為了與Commerce 2.4.6-p6版相容，擁有Adobe Commerce B2B擴充功能的商家必須升級至[B2B 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)版。

### 套用CVE-2024-34102的Hotfix

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

為了與Commerce 2.4.6-p6版相容，擁有Adobe Commerce B2B擴充功能的商家必須升級至[B2B 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)版。

### 反白顯示

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6 - p5

Adobe Commerce 2.4.6-p5安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需這些修正的最新資訊，請參閱[Adobe安全性公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)。

## 2.4.6 - p4

Adobe Commerce 2.4.6-p4安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)。

### 反白顯示

此版本引進了兩項重要的安全性增強功能：

* **未產生快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 （未產生的快取金鑰是透過範本指示詞語法或`setCacheKey`或`setData`方法設定的金鑰。）
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。<!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**。 Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商戶可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)來控制這個新限制。<!-- AC-8753 -->

## 2.4.6 - p3

Adobe Commerce 2.4.6-p3安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性修正的最新資訊，請參閱[Adobe安全性公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)。

### 反白顯示

此發行版本引入新的全頁快取組態設定，有助於減輕與`{BASE-URL}/page_cache/block/esi HTTP`端點相關的風險。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;組態設定會設定此端點的`handles`引數值，此引數會決定每個API允許的控點數目上限。 此屬性的預設值為100。 商戶可從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**&#x200B;變更此值。<!-- AC-9113 -->

### 此版本中包含的Hotfix

Adobe Commerce 2.4.6-p3包含修補程式ACSD-51892所修正的效能降低解析度。 此修補程式解決的問題不會影響商家，相關說明請參閱[ACSD-51892：設定檔載入多次的效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html)知識庫文章。

### 已知問題

**問題**： Adobe Commerce在Composer從`wrong checksum`下載期間顯示`repo.magento.com`錯誤，且封裝下載已中斷。 此問題可能發生於下載發行前期間可用的發行套件期間，而且是由重新封裝`magento/module-page-cache`套件所造成。

**因應措施**：在下載期間看到此錯誤的商家可執行下列步驟：

1) 刪除專案內的`/vendor`目錄（如果存在）。
2) 執行`bin/magento composer update magento/module-page-cache`命令。 這個命令只會更新`page cache`封裝。

如果檢查值問題持續發生，請先移除`composer.lock`檔案，再重新執行`bin/magento composer update`命令以更新每個封裝。

## 2.4.6 - p2

Adobe Commerce 2.4.6-p2安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也提供安全性增強功能，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source 2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[jQuery UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)知識庫文章所指定的修補程式。

### 反白顯示

`fastcgi_pass`檔案中`nginx.sample`的值已傳回至它之前（2.4.6-p1之前）的`fastcgi_backend`值。 在Adobe Commerce 2.4.6-p1中，此值無意間變更為`php-fpm:9000`。

### 此版本中包含的Hotfix

Adobe Commerce 2.4.6-p2包含修補程式ACSD-51892所解決之效能降低的解析度。 此修補程式解決的問題不會影響商家，相關說明請參閱[ACSD-51892：設定檔載入多次的效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html)知識庫文章。

## 2.4.6 - p1

Adobe Commerce 2.4.6-p1安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能和平台升級，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source 2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[查詢UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)知識庫文章所指定的修補程式。

#### 反白顯示

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點的預設行為已變更。 依預設，API現在一律會傳回`true`。 商家可以啟用原始行為，如果電子郵件不存在於資料庫中，則會傳回`true`；如果存在，則會傳回`false`。<!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **清漆快取7.3支援**。 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7.2.x版本仍維持相容性，但Adobe建議僅搭配清漆快取版本7.3或版本6.0 LTS使用Adobe Commerce 2.4.6-p1。

* **RabbitMQ 3.11支援**。 此版本相容於最新版RabbitMQ 3.11。與RabbitMQ 3.9的相容性維持不變（2023年8月之前提供支援），但Adobe建議僅將Adobe Commerce 2.4.6-p1與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**。 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括`moment.js`程式庫(v2.29.4)、`jQuery UI`程式庫(v1.13.2)和`jQuery`驗證外掛程式程式庫(v1.19.5)。

### 已知問題

* `nginx.sample`檔案不慎更新為變更，將`fastcgi_pass`的值從`fastcgi_backend`修改為`php-fpm:9000`。 此變更可以安全地還原或忽略。<!-- AC-8992 -->

* 遺失B2B安全性套件的相依性會在安裝或升級B2B擴充功能至1.4.0時造成下列安裝錯誤。

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  此問題可透過為具有[穩定性標籤](https://getcomposer.org/doc/04-schema.md#package-links)的B2B安全性套件新增手動相依性來解決。 如需詳細資訊，請參閱[B2B發行說明](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue)。

<!-- Last updated from includes: 2025-10-06 13:12:34 -->
