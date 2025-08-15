---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7安全性增強功能

* **已新增子資源完整性(SRI)支援**，以符合PCI 4.0對驗證付款頁面上指令碼完整性的要求。 子資源完整性(SRI)支援為駐留在本機檔案系統中的所有JavaScript資產提供完整性雜湊。 預設SRI功能僅在管理員和店面區域的付款頁面上實作。 不過，商家可以將預設設定延伸至其他頁面。 請參閱[Commerce PHP開發人員指南](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/)._中的_&#x200B;子資源完整性<!--AC-1153-->

* **內容安全性原則(CSP)的變更**—Adobe Commerce內容安全性原則(CSP)的組態更新和增強功能，以符合PCI 4.0的要求。 如需詳細資訊，請參閱[Commerce PHP Developer Guide](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)中的&#x200B;_內容安全性原則_。<!--AC-11513-->

   * Commerce管理員和店面區域的付款頁面的預設CSP設定現在是`restrict`模式。 對於所有其他頁面，預設設定為`report-only`模式。  在2.4.7之前的發行版本中，所有頁面的CSP都設定為`report-only`模式。

   * 新增Nonce提供者，允許在CSP中執行內嵌指令碼。 Nonce提供者可協助為每個請求產生唯一的Nonce字串。 這些字串接著會附加至CSP標頭。

   * 新增選項，可設定自訂URI以報告「管理員」中「建立訂單」頁面的CSP違規以及店面中的「結帳」頁面。 您可以從管理員新增設定，或將URI新增至`config.xml`檔案。

     >[!NOTE]
     >
     >將CSP設定更新為`restrict`模式可能會封鎖管理員和店面中付款頁面上的現有內嵌指令碼，這會在頁面載入時導致下列瀏覽器錯誤： `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`。 更新白名單設定以允許必要的指令碼來修正這些錯誤。 請參閱[Commerce PHP開發人員指南](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting)中的&#x200B;_疑難排解_。
