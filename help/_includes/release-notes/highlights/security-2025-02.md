---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# 2025年2月安全性修補程式重點說明

此版本包含下列重點專案：

* **管理加密金鑰並重新加密資料** — 重新設計管理加密金鑰以提升使用性，並消除先前的限制和錯誤。<!-- AC-12679 -->

  新的CLI命令現在可用於[變更](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/encryption-key)金鑰和[重新加密](https://developer.adobe.com/commerce/php/development/security/data-encryption/)特定系統組態、付款和自訂欄位資料。 此版本不再支援變更管理員UI中的索引鍵。 您必須使用CLI指令。

* **修正[CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** — 解決授權漏洞。

  此修正也可作為獨立修補程式使用。 如需詳細資訊，請參閱[知識庫文章](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08)。<!-- AC-12755 -->

* **TinyMCE版本降級**—TinyMCE相依性已從版本7降級至6.8.5，以解決授權相容性問題。

  Adobe會評估替代開放原始碼WYSIWYG編輯器，此變更可確保持續法規遵循。
