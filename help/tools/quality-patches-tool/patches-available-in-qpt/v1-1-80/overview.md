---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.80
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.80中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 016a56af24e8e4ff127c54713e5fa45ab9fca826
workflow-type: tm+mt
source-wordcount: 461
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.80

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.80中可用修補程式所修正問題的詳細說明。

QPT v1.1.80包含下列修補程式：

1. **ACP2E-4239**：修正由於選取的日期、儲存的UTC值和設定的存放區時區之間的時區差異，使用日期屬性的管理員格線篩選器傳回錯誤結果的問題。
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**：修正在&#x200B;**[!UICONTROL Login as Customer]**&#x200B;流程期間`quote`資料庫表格中建立Null引號記錄的問題。
1. **ACP2E-4481**：修正取消訂單後，無法正確重新計算套件組合產品可銷售性的問題。
1. **ACP2E-4488**：修正屬性集大的產品在[!UICONTROL Admin]中儲存或編輯產品速度緩慢的問題。
1. **ACP2E-4493**：修正啟用非同步索引時，銷售訂單封存格線顯示不正確訂單狀態的問題。
1. **ACP2E-4496**：修正Analytics cron工作在執行期間導致效能降低，進而改善整體系統效能的問題。
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**：修正URL中包含商店程式碼時，店面沒有載入預留位置影像的問題。
1. **ACP2E-4552**：修正GraphQL回應中未傳回公司狀態的問題。
1. **ACP2E-4610**：修正`sales_clean_quotes` cron工作發生效能問題的問題。
1. **ACP2E-4615**：修正線上訂單退款失敗並出現PayPal錯誤的問題，指出&#x200B;*PayPal閘道拒絕要求。 內部錯誤。*。
1. **ACP2E-4626**：修正部分Storefront JavaScript檔案被要求並執行兩次，而造成間歇性重複載入和不穩定行為的問題。
1. **ACP2E-4653**：修正透過REST API擷取或更新規則時，**[!UICONTROL Category (Parent Only)]**&#x200B;和&#x200B;**[!UICONTROL Category (Children Only)]**&#x200B;的&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;條件屬性範圍未公開的問題。
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**：修正店面產品頁面的Weight屬性在&#x200B;**[!UICONTROL Additional Information]**&#x200B;或&#x200B;**[!UICONTROL More Information]**&#x200B;區段中只顯示原始數值而沒有設定測量單位（lbs或kgs）的問題。
1. **ACP2E-4156**：修正REST API中的送貨地址驗證不符合[!UICONTROL Admin]中定義的屬性組態的問題。
1. **ACP2E-4808**：修正店面產品頁面的Weight屬性在&#x200B;**[!UICONTROL Additional Information]**&#x200B;或&#x200B;**[!UICONTROL More Information]**&#x200B;區段中只顯示原始數值而沒有設定測量單位（lbs或kgs）的問題。
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**：修正[!DNL REST] API中的送貨地址驗證未遵循Admin中定義的屬性組態的問題。
1. **ACP2E-4813**：修正某些產品在結帳時無法使用USPS送貨方法，且送貨預估不正確的問題，包括分割成多個套件的訂單。
1. **ACSD-53502**：修正在iOS [!DNL Safari]中，由於遞回呼叫New Relic監視指令碼而導致&#x200B;**[!UICONTROL Add to Cart]**&#x200B;在店面間歇性失敗而導致頁面重新載入的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
