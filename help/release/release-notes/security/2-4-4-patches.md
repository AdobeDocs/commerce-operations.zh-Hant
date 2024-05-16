---
title: Adobe Commerce 2.4.4安全性修補程式的發行說明
description: 瞭解Adobe Commerce 2.4.4版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Adobe Commerce 2.4.4安全性修補程式發行說明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4 - p8

Adobe Commerce 2.4.4-p8安全性版本為Adobe Commerce 2.4.4部署提供安全性錯誤修正。 這些更新會修正先前版本中發現的漏洞。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4 - p7

Adobe Commerce 2.4.4-p7安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### 安全性重點專案

此版本引進了兩項重要的安全性增強功能：

* **非產生之快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 (未產生的快取索引鍵是透過範本指令語法或 `setCacheKey` 或 `setData` 方法。)
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。 <!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**. Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以控制此新限制。 <!-- AC-8753 -->

## 2.4.4 - p6

Adobe Commerce 2.4.4-p6安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

### 安全性反白顯示

此發行版本引進新的全頁快取設定值，有助於降低與相關的風險。 `{BASE-URL}/page_cache/block/esi HTTP` 端點。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的 **[!UICONTROL Handles Param]** 組態設定會設定此端點的值 `handles` 引數，決定每個API允許的最大控制代碼數量。 此屬性的預設值為100。 商家可以從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)。 <!-- AC-9113 -->

### 已知問題

**問題**：Adobe Commerce顯示 **錯誤的總和檢查碼** Composer從下載時發生錯誤 `repo.magento.com`，且封裝下載作業中斷。 在下載發行前版本中提供的發行套件期間可能會發生此問題，此問題的原因是對套件重新封裝 `magento/module-page-cache` 封裝。

**因應措施**：在下載期間看到此錯誤的商家可執行這些步驟：

1) 刪除 `/vendor` 專案內的目錄（如果有的話）。
2) 執行 `bin/magento composer update magento/module-page-cache` 命令。 這個命令只會更新 `page cache` 封裝。

如果檢查值問題持續發生，請移除 `composer.lock` 重新執行之前的檔案 `bin/magento composer update` 更新每個套件的命令。

## 2.4.4 - p5

Adobe Commerce 2.4.4-p5安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI` 資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用 [jQuery UI安全漏洞2.4.4、2.4.5和2.4.6版的CVE-2022-31160修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知識庫文章。

## 2.4.4 - p4

Adobe Commerce 2.4.4-p4安全性版本針對先前版本中發現的弱點提供安全性錯誤修正。 此版本也包含安全性增強功能和平台升級，以更符合最新的安全性最佳實務。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### 套用修補程式以解決安全性弱點jQuery-UI程式庫中的CVE-2022-31160

`jQuery-UI` 資料庫1.13.1版具有已知的安全性弱點(CVE-2022-31160)，會影響多個版本的Adobe Commerce和Magento Open Source。 此程式庫相依於Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。執行受影響部署的商戶應套用 [jQuery UI安全漏洞2.4.4、2.4.5和2.4.6版的CVE-2022-31160修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知識庫文章。

### 安全性反白顯示

的預設行為 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點已變更。 依預設，API現在一律會傳回 `true`. 商家可以啟用原始行為，即 `true` 如果電子郵件不存在於資料庫中，並且 `false` 如果它存在。 <!-- AC-6695 -->

### 平台升級

此版本的平台升級可改善對最新安全性最佳實務的合規性。

* **支援清漆快取7.3**. 此版本相容於最新版的Varnish Cache 7.3。6.0.x和7u.2.x版本仍維持相容性，但Adobe建議僅將Adobe Commerce 2.4.4-p4與Varnish Cache 7.3或6.0版LTS搭配使用。

* **RabbitMQ 3.11支援**. 此版本與最新版RabbitMQ 3.11相容。RabbitMQ 3.9仍支援相容性至2023年8月，但Adobe建議僅將Adobe Commerce 2.4.4-p4與RabbitMQ 3.11搭配使用。

* **JavaScript資料庫**. 過時的JavaScript程式庫已升級至最新的次要或修補程式版本，包括 `moment.js` 資料庫(v2.29.4)， `jQuery UI` 資料庫(v1.13.2)和 `jQuery` 驗證外掛程式庫(v1.19.5)。

## 2.4.4 - p3

Adobe Commerce 2.4.4-p3安全性版本針對先前版本中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4 - p2

Adobe Commerce 2.4.4-p2安全性版本針對先前版本中發現的弱點提供修正。 其中一項修正包括建立新的組態設定。 此 **如果電子郵件已變更，則要求電子郵件確認** 組態設定可讓管理員在管理員使用者變更其電子郵件地址時，要求電子郵件確認。 <!-- AC-6292-->

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### 套用AC-3022.patch以繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應適用 `AC-3022.patch` 儘早繼續提供DHL作為貨運業者。 請參閱 [套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) 知識庫文章，瞭解如何下載及安裝修補程式。

## 2.4.4 - p1

Adobe Commerce 2.4.4-p1安全性版本針對先前版本中發現的弱點提供修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱 [Adobe安全性公告](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### 套用 `AC-3022.patch` 繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應適用 `AC-3022.patch` 儘早繼續提供DHL作為貨運業者。 請參閱 [套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 知識庫文章，瞭解如何下載及安裝修補程式。

### 安全性重點專案

此版本的安全性改善專案可改善對最新安全性最佳實務的合規性，包括：

* ACL資源已新增至詳細目錄。
* 已增強詳細目錄範本安全性。

### 已知問題

**問題**：在2.4.4-p1套件上執行時，Web API和整合測試會顯示此錯誤： `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **因應措施**：執行以安裝先前版本的Monolog `require monolog/monolog:2.6.0` 命令。 <!-- AC-3651-->

**問題**：商家在從Adobe Commerce 2.4.4升級至Adobe Commerce 2.4.4-p1時可能會注意到套件版本降級通知。 可以忽略這些訊息。 套件版本中的差異是因為產生套件期間發生異常所導致。 沒有任何產品功能受到影響。 請參閱 [從2.4.4升級至2.4.4-p1後，套件已降級](https://support.magento.com/hc/en-us/articles/8214752983949) 知識庫文章，討論受影響的案例與因應措施。

