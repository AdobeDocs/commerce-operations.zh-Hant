---
title: Adobe Commerce 2.4.6安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.6版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---


# Adobe Commerce 2.4.6安全性修補程式的發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

Adobe Commerce 2.4.6-p6安全性版本針對2.4.6舊版中已發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### 安全性熒光燈

為了與Commerce 2.4.6-p6版相容，擁有Adobe Commerce B2B擴充功能的商家必須升級至 [B2B 1.4.2版 — p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).


### 其他安全性增強功能

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

Adobe Commerce 2.4.6-p5安全性版本針對2.4.6舊版中發現的漏洞提供安全性錯誤修正。

如需這些修正的最新資訊，請參閱 [Adobe安全性公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

Adobe Commerce 2.4.6-p4安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### 安全性重點專案

此版本引進了兩項重要的安全性增強功能：

* **非產生之快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 (未產生的快取索引鍵是透過範本指令語法或 `setCacheKey` 或 `setData` 方法。)
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。  <!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**. Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以控制此新限制。 <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

Adobe Commerce 2.4.6-p3安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性修正的最新資訊，請參閱 [Adobe安全性公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### 安全性重點專案

此發行版本引進新的全頁快取設定值，有助於降低與相關的風險。 `{BASE-URL}/page_cache/block/esi HTTP` 端點。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的 **[!UICONTROL Handles Param]** 組態設定會設定此端點的值 `handles` 引數，決定每個API允許的最大控制代碼數量。 此屬性的預設值為100。 商家可以從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### 此版本中包含的Hotfix

Adobe Commerce 2.4.6-p3包含修補程式ACSD-51892所修正的效能降低解析度。 此修補程式所解決的問題不會影響商家，相關說明請參閱 [ACSD-51892：設定檔案載入多次的效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) 知識庫文章。

### 已知問題

**問題**：Adobe Commerce顯示 `wrong checksum` Composer從下載時發生錯誤 `repo.magento.com`，且封裝下載作業中斷。 此問題可能發生於下載發行前期間提供的發行套件期間，而且是由重新封裝造成的 `magento/module-page-cache` 封裝。

**因應措施**：在下載期間看到此錯誤的商家可執行這些步驟：

1) 刪除 `/vendor` 專案內的目錄（如果有的話）。
2) 執行 `bin/magento composer update magento/module-page-cache` 命令。 這個命令只會更新 `page cache` 封裝。

如果檢查值問題持續發生，請移除 `composer.lock` 重新執行之前的檔案 `bin/magento composer update` 更新每個套件的命令。

## 2.4.6 - p2

Adobe Commerce 2.4.6-p2安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也提供安全性增強功能，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI` 資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用 [jQuery UI安全漏洞2.4.4、2.4.5和2.4.6版的CVE-2022-31160修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知識庫文章。

### 安全性反白顯示

的值 `fastcgi_pass` 在 `nginx.sample` 檔案已傳回至其先前的（2.4.6-p1以前版本）值 `fastcgi_backend`. 此值不慎變更為 `php-fpm:9000` 在Adobe Commerce 2.4.6-p1中。

### 此版本中包含的Hotfix

Adobe Commerce 2.4.6-p2包含修補程式ACSD-51892所解決之效能降低的解析度。 此修補程式所解決的問題不會影響商家，相關說明請參閱 [ACSD-51892：設定檔案載入多次的效能問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) 知識庫文章。

## Adobe Commerce 2.4.6-p1

Adobe Commerce 2.4.6-p1安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能和平台升級，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI` 資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用 [2.4.4、2.4.5和2.4.6版的查詢UI安全漏洞CVE-2022-31160修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知識庫文章。

#### 安全性反白顯示

的預設行為 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點已變更。 依預設，API現在一律會傳回 `true`. 商家可以啟用原始行為，即 `true` 如果電子郵件不存在於資料庫中，並且 `false` 如果它存在。 <!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **支援清漆快取7.3**. 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7.2.x版本仍維持相容性，但Adobe建議使用Adobe Commerce 2.4.6-p1，僅搭配Varnish Cache 7.3或6.0版LTS。

* **RabbitMQ 3.11支援**. 此版本與最新版RabbitMQ 3.11相容。RabbitMQ 3.9仍支援相容性至2023年8月，但Adobe建議僅將Adobe Commerce 2.4.6-p1與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**. 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括 `moment.js` 資料庫(v2.29.4)， `jQuery UI` 資料庫(v1.13.2)和 `jQuery` 驗證外掛程式庫(v1.19.5)。

### 已知問題

* 此 `nginx.sample` 檔案無意中更新而進行了變更，並修改了 `fastcgi_pass` 從 `fastcgi_backend` 至 `php-fpm:9000`. 此變更可以安全地還原或忽略。 <!-- AC-8992 -->

* 遺失B2B安全性套件的相依性會在安裝或升級B2B擴充功能至1.4.0時造成下列安裝錯誤。

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  此問題可透過為具有的B2B安全性套件新增手動相依性來解決 [穩定性標籤](https://getcomposer.org/doc/04-schema.md#package-links). 如需詳細資訊，請參閱 [B2B發行說明](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
