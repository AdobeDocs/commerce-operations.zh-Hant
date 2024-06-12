---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7安全性增強功能

目前尚未發生與這些問題相關的已確認攻擊。 但是，某些漏洞可能會被用來存取客戶資訊或接管管理員工作階段。 這些問題大多需要攻擊者先取得Admin的存取權。 因此，我們提醒您採取一切必要步驟來保護您的管理員，包括但不限於這些工作：

* IP允許清單
* [雙因素驗證](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* 使用VPN
* 使用唯一位置，而非 `/admin`
* 良好的密碼衛生

此版本的安全性改善專案可改善對最新安全性最佳實務的合規性。

* **非產生之快取金鑰的行為變更**：

   * 區塊的非產生快取金鑰現在包含與自動產生之金鑰的前置詞不同的前置詞。 (未產生的快取索引鍵是透過範本指令語法或 `setCacheKey` 或 `setData` 方法。)
   * 區塊未產生的快取金鑰現在只能包含字母、數字、連字型大小(-)和底線字元(_)。  <!-- AC-9831 -->

* **自動產生優惠券代碼數目的限制**. Commerce現在會限制自動產生的抵用券代碼數量。 預設最大值為250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 組態選項(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以防止許多優惠券讓系統不堪重負。 <!-- AC-8753 -->

* **最佳化預設管理員URL產生程式**. 預設管理員URL的產生已針對增加的隨機性而最佳化，使產生的URL較難預測。 <!-- AC-9028 -->

* **新增子資源完整性(SRI)支援** 以符合PCI 4.0的要求，驗證付款頁面上的指令碼完整性。 子資源完整性(SRI)支援為駐留在本機檔案系統中的所有JavaScript資產提供完整性雜湊。 預設SRI功能僅在管理員和店面區域的付款頁面上實作。 不過，商家可以將預設設定延伸至其他頁面。 另請參閱 [子資源完整性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) 在 _Commerce PHP開發人員指南_.<!--AC-1153-->

* **內容安全性原則(CSP)的變更**—Adobe Commerce內容安全性原則(CSP)的設定更新和增強功能，以符合PCI 4.0需求。 如需詳細資訊，請參閱 [內容安全性原則](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _Commerce PHP開發人員指南_. <!--AC-11513-->

   * Commerce管理員和店面區域的付款頁面的預設CSP設定現在為 `restrict` 模式。 對於所有其他頁面，預設設定為 `report-only` 模式。  在2.4.7之前的版本中，CSP是設定在 `report-only` 模式。

   * 新增Nonce提供者，允許在CSP中執行內嵌指令碼。 Nonce提供者可協助為每個請求產生唯一的Nonce字串。 這些字串接著會附加至CSP標頭。

   * 新增選項，可設定自訂URI以報告「管理員」中「建立訂單」頁面的CSP違規以及店面中的「結帳」頁面。 您可以從管理員新增設定，或將URI新增至 `config.xml` 檔案。

     >[!NOTE]
     >
     >將CSP設定更新至 `restrict` 模式可能會在「管理員」和「店面」的付款頁面上封鎖現有的內嵌指令碼，這會在頁面載入時導致下列瀏覽器錯誤： `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 更新白名單設定以允許必要的指令碼來修正這些錯誤。 另請參閱 [疑難排除](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) 在 _Commerce PHP開發人員指南_.

* 新的全頁快取設定有助於降低與HTTP相關的風險 `{BASE-URL}/page_cache/block/esi` 端點。 此端點支援來自Commerce配置控點和區塊結構的不受限制、動態載入的內容片段。 新的 **[!UICONTROL Handles params size]** 組態設定會設定此端點的值 `handles` 引數，決定每個API允許的最大控制代碼數量。 此屬性的預設值為100。 商家可以從管理員(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**)。 另請參閱 [設定Commerce應用程式以使用Varnish](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **透過REST和GraphQL API傳輸的付款資訊的原生費率限制**. 商戶現在可以 [設定速率限制](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) 以取得使用REST和GraphQL傳輸的付款資訊。 此新增的保護層可支援防止梳理攻擊，並可能會減少同時測試許多信用卡號碼的梳理攻擊的數量。 這是現有REST端點預設行為的變更。 另請參閱 [速率限制](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* 的預設行為 [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查詢和([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端點已變更。 依預設，API現在一律會傳回 `true`. 商家可以透過設定 *[啟用來賓簽出登入](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* 管理員中的選項，用於 `yes`，但這麼做可能會將客戶資訊公開給未經驗證的使用者。
