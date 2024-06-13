---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7安全性增強功能

* **新增子資源完整性(SRI)支援** 以符合PCI 4.0的要求，驗證付款頁面上的指令碼完整性。 子資源完整性(SRI)支援為駐留在本機檔案系統中的所有JavaScript資產提供完整性雜湊。 預設SRI功能僅在管理員和店面區域的付款頁面上實作。 不過，商家可以將預設設定延伸至其他頁面。 另請參閱 [子資源完整性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) 在 _Commerce PHP開發人員指南_.<!--AC-1153-->

* **內容安全性原則(CSP)的變更**—Adobe Commerce內容安全性原則(CSP)的設定更新和增強功能，以符合PCI 4.0需求。 如需詳細資訊，請參閱 [內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _Commerce PHP開發人員指南_. <!--AC-11513-->

   * Commerce管理員和店面區域的付款頁面的預設CSP設定現在為 `restrict` 模式。 對於所有其他頁面，預設設定為 `report-only` 模式。  在2.4.7之前的版本中，CSP是設定在 `report-only` 模式。

   * 新增Nonce提供者，允許在CSP中執行內嵌指令碼。 Nonce提供者可協助為每個請求產生唯一的Nonce字串。 這些字串接著會附加至CSP標頭。

   * 新增選項，可設定自訂URI以報告「管理員」中「建立訂單」頁面的CSP違規以及店面中的「結帳」頁面。 您可以從管理員新增設定，或將URI新增至 `config.xml` 檔案。

     >[!NOTE]
     >
     >將CSP設定更新至 `restrict` 模式可能會在「管理員」和「店面」的付款頁面上封鎖現有的內嵌指令碼，這會在頁面載入時導致下列瀏覽器錯誤： `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 更新白名單設定以允許必要的指令碼來修正這些錯誤。 另請參閱 [疑難排除](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) 在 _Commerce PHP開發人員指南_.
