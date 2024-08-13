---
title: Adobe Commerce 2.4.4安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.4版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 0%

---


# Adobe Commerce 2.4.4安全性修補程式的發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p10

Adobe Commerce 2.4.4-p10安全性版本針對2.4.4舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 反白顯示

{{$include /help/_includes/release-notes/2024-08/security.md}}

### 此版本中包含的Hotfix

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.4 - p9

Adobe Commerce 2.4.4-p9安全性版本針對2.4.4先前版本中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 套用CVE-2024-34102的Hotfix

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### 平台升級

* **MariaDB 10.5支援**。 此修補程式發行版本引入與MariaDB 10.5版的相容性。Adobe Commerce仍與MariaDB 10.4版相容，但Adobe建議使用Adobe Commerce 2.4.4-p9以及所有即將發行的2.4.4僅限安全性修補程式版本，僅與MariaDB 10.5版相容，因為MariaDB 10.4維護作業將於2024年6月18日結束。<!--AC-11530-->

### 反白顯示

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4 - p8

Adobe Commerce 2.4.4-p8安全性版本為Adobe Commerce 2.4.4部署提供安全性錯誤修正。 這些更新會修正先前版本中發現的漏洞。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)。

## 2.4.4 - p7

Adobe Commerce 2.4.4-p7安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)。

### 反白顯示

此版本引進了兩項重要的安全性增強功能：

* **未產生快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 （未產生的快取金鑰是透過範本指示詞語法或`setCacheKey`或`setData`方法設定的金鑰。）
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。<!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**。 Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商戶可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)來控制這個新限制。<!-- AC-8753 -->

## 2.4.4 - p6

Adobe Commerce 2.4.4-p6安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)。

此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

### 反白顯示

此發行版本引入新的全頁快取組態設定，有助於減輕與`{BASE-URL}/page_cache/block/esi HTTP`端點相關的風險。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;組態設定會設定此端點的`handles`引數值，此引數會決定每個API允許的控點數目上限。 此屬性的預設值為100。 商戶可從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)變更此值。<!-- AC-9113 -->

### 已知問題

**問題**： Adobe Commerce在Composer從`repo.magento.com`下載期間顯示&#x200B;**錯誤的總和檢查碼**&#x200B;錯誤，且封裝下載已中斷。 此問題可能發生於下載發行前期間提供的發行套件期間，而且是由重新封裝`magento/module-page-cache`套件所造成。

**因應措施**：在下載期間看到此錯誤的商家可執行下列步驟：

1) 刪除專案內的`/vendor`目錄（如果存在）。
2) 執行`bin/magento composer update magento/module-page-cache`命令。 這個命令只會更新`page cache`封裝。

如果檢查值問題持續發生，請先移除`composer.lock`檔案，再重新執行`bin/magento composer update`命令以更新每個封裝。

## 2.4.4 - p5

Adobe Commerce 2.4.4-p5安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[jQuery UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)知識庫文章所指定的修補程式。

## 2.4.4 - p4

Adobe Commerce 2.4.4-p4安全性版本針對先前版本中發現的弱點提供安全性錯誤修正。 此版本也包含安全性增強功能和平台升級，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)。

### 套用CVE-2022-31160的Hotfix

`jQuery-UI`資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用[jQuery UI安全性弱點CVE-2022-31160針對2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)知識庫文章所指定的修補程式。

### 反白顯示

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點的預設行為已變更。 依預設，API現在一律會傳回`true`。 商家可以啟用原始行為，如果電子郵件不存在於資料庫中，則會傳回`true`；如果存在，則會傳回`false`。<!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **清漆快取7.3支援**。 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7u.2.x版本仍維持相容性，但Adobe建議僅將Adobe Commerce 2.4.4-p4與Varnish Cache 7.3或6.0版LTS搭配使用。

* **RabbitMQ 3.11支援**。 此版本與最新版RabbitMQ 3.11相容。RabbitMQ 3.9仍支援相容性至2023年8月，但Adobe建議僅將Adobe Commerce 2.4.4-p4與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**。 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括`moment.js`程式庫(v2.29.4)、`jQuery UI`程式庫(v1.13.2)和`jQuery`驗證外掛程式程式庫(v1.19.5)。

## 2.4.4 - p3

Adobe Commerce 2.4.4-p3安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html)。

## 2.4.4 - p2

Adobe Commerce 2.4.4-p2安全性版本針對先前版本中發現的弱點提供修正。 其中一項修正包括建立新的組態設定。 如果電子郵件已變更，**需要電子郵件確認**&#x200B;組態設定可讓管理員在管理員使用者變更其電子郵件地址時，需要電子郵件確認。<!-- AC-6292-->

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html)。

### 套用AC-3022.patch以繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481)知識庫文章，以取得有關下載和安裝修補程式的資訊。

## 2.4.4 - p1

Adobe Commerce 2.4.4-p1安全性版本針對先前版本中發現的弱點提供修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告](https://helpx.adobe.com/security/products/magento/apsb22-38.html)。t

### 套用`AC-3022.patch`以繼續提供DHL作為運送承運商

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知識庫文章，以取得有關下載和安裝修補程式的資訊。

### 反白顯示

此版本的安全性改善專案可改善對最新安全性最佳實務的合規性，包括：

* ACL資源已新增至詳細目錄。
* 已增強詳細目錄範本安全性。

### 已知問題

**問題**：在2.4.4-p1封裝上執行時，Web API和整合測試會顯示此錯誤： `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`。 **因應措施**：執行`require monolog/monolog:2.6.0`命令以安裝舊版的Monolog。<!-- AC-3651-->

**問題**：商家在從Adobe Commerce 2.4.4升級至Adobe Commerce 2.4.4-p1時，可能會注意到套件版本降級通知。 可以忽略這些訊息。 套件版本中的差異是因為產生套件期間發生異常所導致。 沒有任何產品功能受到影響。 請參閱從2.4.4升級為2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949)知識庫文章後降級的[套件，瞭解受影響的案例和因應措施。
