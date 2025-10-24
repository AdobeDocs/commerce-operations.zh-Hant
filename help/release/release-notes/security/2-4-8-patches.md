---
title: Adobe Commerce 2.4.8安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.7版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Adobe Commerce 2.4.8安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8 - p3

Adobe Commerce 2.4.8-p3安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-94](https://helpx.adobe.com/tw/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 反白顯示

此版本包含下列重點專案：

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* ACP2E-3874的修正：訂單詳細資料的REST API回應現在包含`base_row_total`和`row_total`屬性的正確值，以備已訂購數個相同專案時使用。

* AC-15446的修正：修正`Magento\Framework\Mail\EmailMessage`中`getBodyText()`嘗試在`getTextBody()`上呼叫不存在的`Symfony\Component\Mime\Message`方法的錯誤，確保與Magento 2.4.8-p2和`magento/framework` 103.0.8-p2相容。

{{oct-2025-backports}}

### 已知問題

#### 簽出頁面無法載入static.min.js和mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8 - p2

Adobe Commerce 2.4.8-p2安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-71](https://helpx.adobe.com/tw/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.8 - p1

Adobe Commerce 2.4.8-p1安全性版本針對2.4.8舊版中發現的漏洞提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB25-50](https://helpx.adobe.com/tw/security/products/magento/apsb25-50.html)。

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

CVE-2025-47110和VULN-31547的修正也以獨立修補程式的形式提供。 如需詳細資訊，請參閱[知識庫文章](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
