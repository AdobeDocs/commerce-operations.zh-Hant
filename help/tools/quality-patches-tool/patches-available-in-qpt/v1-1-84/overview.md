---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.84
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.84中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f0b3307638e56d5930753a4123a98ddea6714faa
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.84

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.84中可用修補程式所修正問題的詳細說明。

QPT v1.1.84包含下列修補程式：

1. **ACP2E-4913**：修正因鎖死而造成送貨與開立商業發票作業失敗的問題。
1. **ACP2E-5005**：修正可轉讓報價單中的搭售產品選項數量，在Admin中重新設定搭售產品並編輯數量時，回覆為先前值的問題。
1. **ACP2E-5009**：修正從Magento Open Source移轉至Adobe Commerce的資料未正確移轉類別排程設計變更和產品&#x200B;**[!UICONTROL Special Price]**&#x200B;排程更新，導致移轉期間遺失或略過部分排程更新的問題，並改善移轉效能。
1. **ACP2E-5017**：修正當客戶未指派給公司時，透過GraphQL查詢客戶角色傳回&#x200B;*內部伺服器錯誤*&#x200B;的問題。
1. **ACP2E-5027**：修正當啟用檔案鎖定時，索引器停滯在回圈中且重新索引未完成的問題。
1. **ACP2E-5029**：修正手動重新同步之前，**[!DNL Live Search]**&#x200B;中未顯示目錄價格規則變更的問題。
1. **ACP2E-5041**：修正了在排程更新期間儲存產品，導致在更新結束後店面顯示一般價格而非&#x200B;**[!UICONTROL Special Price]**&#x200B;的問題。
1. **ACP2E-5059**：修正客戶收到相同訂單的重複訂單確認電子郵件的問題。
1. **ACP2E-5122**：修正例外狀況記錄檔中，針對購物車的GraphQL要求所處理的錯誤，不正確記錄為應用程式錯誤的問題。
1. **ACP2E-5143**：修正僅請求路由中繼資料時，GraphQL路由查詢呈現完整CMS頁面內容的問題，增加包含Page Builder Widget的CMS頁面的資料庫查詢。
1. **ACP2E-5183**：修正編譯使用`@magento_import`指示詞的`LESS`檔案時，PHP 8.5上的靜態內容部署失敗的問題。
1. **ACP2E-5242**：修正將專案新增至購物車時，檢查產品可用性顯示錯誤，指出找不到網站的問題。
1. **ACP2E-5263**：修正將產品匯出至CSV檔案後，無法再包含所有產品，而造成檔案不完整的問題。
1. **ACP2E-5034**：修正當選取送貨方式後重新計算報價時，可轉讓的報價管理錯誤地將總計重設為&#x200B;*零*&#x200B;的問題，捨棄透過Admin中的&#x200B;**[!UICONTROL Configure]**&#x200B;動作進行的套裝產品選項數量更新，且無法在報價小計中正確反映套用至動態價格套裝產品的料號層級折扣。
1. **ACP2E-4741**：修正連結為[!UICONTROL Related Product]、[!UICONTROL Up-Sell]或交叉銷售的產品儲存後，產品從店面消失的問題，同時非預設庫存和來源正在使用中。
1. **ACP2E-5079**：修正當客戶帳戶在全球共用時，評估指派給多個網站的客戶區段只會從第一個網站傳回相符客戶的問題。
1. **ACP2E-5127**：修正在「管理員」面板中使用非預設地區設定編輯公司帳戶時，其&#x200B;**[!UICONTROL Credit Limit]**&#x200B;會重設為&#x200B;*zero*&#x200B;的問題。
1. **AC-15494**：修正產品查詢傳回帶有HTML逸出特殊字元（而非其原始字元）的產品名稱的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
