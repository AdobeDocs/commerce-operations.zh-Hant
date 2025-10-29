---
title: Adobe Commerce 2.4.3安全性修補程式的發行說明
description: 瞭解Adobe Commerce 2.4.3版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 2e62c49dd0c338f0913ce5f725f396c2cfa95122
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Adobe Commerce 2.4.3安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Adobe Commerce 2.4.3-p3安全性版本針對先前版本2.4.3已發現的漏洞提供安全性修正。此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html)。

### 套用AC-3022.patch以繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知識庫文章，以取得有關下載和安裝修補程式的資訊。

### 安全性重點專案

* ACL資源已新增至詳細目錄。
* 已增強詳細目錄範本安全性。



## Adobe Commerce 2.4.3-p2

Adobe Commerce 2.4.3-p2安全性版本針對先前版本中發現的弱點提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html)。  此修補程式發行版本也解決了`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`和`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`所處理的弱點。


### 套用AC-3022.patch以繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知識庫文章，以取得有關下載和安裝修補程式的資訊。

### 安全性重點專案

* 在2.3.4中，已棄用電子郵件變數，這是安全性風險降低的一部分，以支援更嚴格的變數語法。 此舊版行為已完全移除，作為該安全性風險緩解措施的延續。

  因此，在舊版中有效的電子郵件或電子報範本在升級至Adobe Commerce 2.4.3-p2後可能無法正常運作。 受影響的範本包括自訂模組或第三方擴充功能的管理員覆寫、主題、子主題和範本。 即使使用[Upgrade相容性工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en)修正已棄用的使用方式，您的部署仍可能受到影響。 請參閱[移轉自訂電子郵件範本](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/)，以取得移轉受影響範本的潛在影響和准則相關資訊。

* OAuth存取權杖和密碼重設權杖現在儲存於資料庫時經過加密。<!-- AC-520 1323-->

* 已加強驗證，以防止上傳非英數字元的副檔名。<!-- AC-479-->

* Adobe Commerce處於生產模式時，Swagger現在預設為停用。<!-- AC-1450-->

* 開發人員現在可以根據每個端點，為Adobe Commerce RESTful端點接受的陣列設定大小限制。 檢視[API安全性](https://developer.adobe.com/commerce/webapi/get-started/api-security/)。<!-- AC-465-->

* 新增機制來限制使用者可在系統範圍內透過Web API要求的大小和資源數量，以及覆寫個別模組的預設值。 此增強功能解決`MC-43048__set_rate_limits__2.4.3.patch`所解決的問題。 檢視[API安全性](https://developer.adobe.com/commerce/webapi/get-started/api-security/)。<!-- AC-1120-->


## 2.4.3-p1

Adobe Commerce 2.4.3-p1安全性版本針對先前版本(Adobe Commerce 2.4.3和Magento Open Source 2.4.3)中發現的漏洞提供安全性錯誤修正。 此版本也包含安全性增強功能，可改善對最新安全性最佳實務的合規性。


如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html)。 此修補程式發行版本也針對[Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html)、[Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)及[Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)廠商開發的擴充功能提供錯誤修正。

### 套用AC-3022.patch以繼續提供DHL作為運送業者

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知識庫文章，以取得有關下載和安裝修補程式的資訊。

### Hotfix

此版本包含下列Hotfix，以及針對先前修補程式版本所發行的所有Hotfix。

* 修補程式`AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`。 請參閱[Adobe Commerce升級2.4.3、2.3.7-p1 PHP嚴重錯誤Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix)知識庫文章，瞭解修補程式和問題的相關資訊。

### 安全性重點專案

已從資料庫&#x200B;**移除**&#x200B;工作階段識別碼。 如果商戶有使用儲存在資料庫中的原始工作階段ID的自訂或安裝擴充功能，則此程式碼變更可能會導致重大變更。<!-- MC-40976-->

**已限制管理員存取媒體集資料夾**。 預設媒體集許可權現在只允許設定明確允許的目錄操作（檢視、上傳、刪除和建立）。 管理員使用者無法再透過在`catalog/category`或`wysiwyg`目錄之外上傳的媒體集存取媒體資產。 管理員如果想要存取媒體資產，必須將其移至明確允許的資料夾，或調整其組態設定。 請參閱[修改媒體櫃資料夾許可權](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/)。<!-- B2B-1897-->

**降低GraphQL查詢複雜度的限制**。 GraphQL允許的查詢複雜度上限已降低，以防止拒絕服務(DOS)攻擊。 檢視[GraphQL安全性組態](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/)。<!-- PWA-1700-->

**此版本已修正最近的滲透測試漏洞**。<!-- MC-42431-->

不支援的來源運算式`unsafe-inline`已從內容安全性原則`frame-ancestors`指示詞中移除。 [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
