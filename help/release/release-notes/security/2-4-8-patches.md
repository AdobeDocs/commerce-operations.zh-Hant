---
title: Adobe Commerce 2.4.8安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.8版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a61409b02e612295fb03a42e22dcfdf5c3eb0e57
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Adobe Commerce 2.4.8安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8 - p5

Adobe Commerce 2.4.8-p5安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB26-49](https://helpx.adobe.com/security/products/magento/apsb26-49.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

#### MariaDB 11.8相容性

Adobe Commerce 2.4.8已經過相容於MariaDB 11.8的驗證，同時仍支援MariaDB 11.4。 此更新解決MariaDB 11.8中引入的SQL行為變更、預設更新和淘汰問題，以維持平台穩定性。

#### OpenSearch 3最新次要版本支援

Adobe Commerce 2.4.8現在支援雲端基礎結構、雲端原生和內部部署上的Adobe Commerce上最新的次要OpenSearch 3版本。 與OpenSearch 2的相容性得以保留。

#### Valkey 9.x LTS支援

Adobe Commerce 2.4.8現在與Valkey 9.x LTS相容，提供雲端基礎結構上的Adobe Commerce所支援的長期支援快取後端選項。

#### RabbitMQ 4.2支援

Adobe Commerce 2.4.8現在與RabbitMQ 4.2相容，後者處理RabbitMQ 4.1支援終止日期排定於2026年2月。 與Apache ActiveMQ Artemis的相容性得以保留，且ActiveMQ仍為此安全性專用發行版本的預設訊息佇列服務。

#### USPS REST API支援

除了舊版Web Tools API外，USPS船運整合現在還支援現代化的RESTful USPS API。 管理員可以從管理員設定中選取要使用的USPS整合API。 此更新會針對USPS網站工具API淘汰進行準備。

#### Magento擁有的Laminas MVC分支

為了解決Laminas MVC淘汰，Adobe Commerce現在使用Magento擁有的`laminas-mvc`復本（發佈為`magento/magento-zf-mvc`）。 此復本可確保持續修補及長期符合Adobe Commerce 2.4.8的安全性規範。

## 2.4.8 - p4

Adobe Commerce 2.4.8-p4安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

#### DHL出貨整合的MyDHL REST API支援

除了現有的DHL Express XML整合之外，DHL出貨整合現在也支援MyDHL REST API。 此更新會與DHL目前的API棧疊一致，並準備淘汰舊版XML API。

#### 新增與最新撰寫器版本的相容性

Adobe Commerce 2.4.8已更新，以支援Composer 2.9.x，同時繼續與Composer 2.2 LTS相容。

## 2.4.8 - p3

Adobe Commerce 2.4.8-p3安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* ACP2E-3874的修正：訂單詳細資料的REST API回應現在包含`base_row_total`和`row_total`屬性的正確值，以備已訂購數個相同專案時使用。

* AC-15446的修正：修正`Magento\Framework\Mail\EmailMessage`中`getBodyText()`嘗試在`Symfony\Component\Mime\Message`上呼叫不存在的`getTextBody()`方法的錯誤，確保與Magento 2.4.8-p2和`magento/framework` 103.0.8-p2相容。

{{oct-2025-backports}}

### 已知問題

#### 簽出頁面無法載入static.min.js和mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8 - p2

Adobe Commerce 2.4.8-p2安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.8 - p1

Adobe Commerce 2.4.8-p1安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

* **API效能增強** — 解決先前安全性修補程式之後引入的大量非同步Web API端點效能降低的問題。<!-- AC-14078 -->

* **CMS封鎖存取修正** — 解決具有受限制許可權（例如僅限銷售存取）的管理員使用者無法檢視[!UICONTROL CMS Blocks]清單頁面的問題。

  以前，這些使用者在安裝先前的安全性修補程式後，由於遺失設定引數而發生錯誤。<!-- AC-14087 -->

* **Cookie限制相容性** — 解決框架中涉及`MAX_NUM_COOKIES`常數的回溯不相容變更。 此更新會還原預期行為，並確保與Cookie限制互動的擴充功能或自訂功能的相容性。<!-- AC-14475 -->

* **非同步作業** — 已限制用於覆寫先前客戶訂單的非同步作業。<!-- AC-13917 -->

* **修正CVE-2025-47110** — 解決電子郵件範本的弱點。<!-- AC-14695 -->

* **VULN-31547的修正** — 解決類別規範連結弱點。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110和VULN-31547的修正也以獨立修補程式的形式提供。 如需詳細資訊，請參閱[知識庫文章](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
