---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.85
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.85中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.85

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.85中可用修補程式所修正問題的詳細說明。

QPT v1.1.85包含下列修補程式：

1. **ACP2E-4929**：修正&#x200B;**[!UICONTROL Compare Products]**&#x200B;頁面上的屬性標籤顯示不同商店檢視（而非目前商店檢視）的翻譯的問題。
1. **ACP2E-5075**：修正固定金額購物車價格規則與類別條件不正確套用折扣（當規則僅符合搭售組合父項產品時）至動態價格搭售組合產品所有子項的問題。
1. **ACP2E-5077**：修正並行的`customerCart`個GraphQL查詢或`POST /V1/carts/mine`個REST要求為尚未擁有作用中購物車的客戶建立重複作用中購物車的問題。
1. **ACP2E-5088**：修正工作階段過期時客戶永久購物車被清除的問題。
1. **ACP2E-3991**：修正使用者端IP位址未正確判斷的問題。
1. **ACP2E-5092**：修正&#x200B;**[!UICONTROL Company Profile]**&#x200B;頁面和管理員客戶編輯頁面在儲存的公司地址之後沒有區域時，在國家/地區新增區域時顯示錯誤的問題。
1. **ACP2E-5124**：修正當&#x200B;**[!UICONTROL Validation Strategy]**&#x200B;設為&#x200B;**[!UICONTROL Stop on Error]**&#x200B;時，驗證失敗後，**[!UICONTROL Import]**&#x200B;按鈕在驗證結果中仍然可用的問題。
1. **AC-17456**：修正在Admin Panel的&#x200B;**[!UICONTROL Design Configuration]**&#x200B;頁面上編輯&#x200B;**[!UICONTROL Global]**&#x200B;範圍時，在PHP 8.4和8.5上傳回&#x200B;*HTTP 500*&#x200B;錯誤的問題。
1. **ACP2E-5212**：修正&#x200B;**[!UICONTROL Quick Order]**&#x200B;接受副檔名為`.csv`的非CSV檔案的問題。
1. **ACP2E-5300**：修正關鍵字在管理面板&#x200B;**[!UICONTROL Orders]**&#x200B;格線中搜尋多個以空格或逗號分隔的訂單編號時，未傳回任何相符訂單的問題。
1. **ACP2E-5354**：修正透過REST API更新客戶時，與公司帳戶相關聯的客戶會在Admin **[!UICONTROL Customers]**&#x200B;格線中出現多次的問題。
1. **ACP2E-5208**：修正&#x200B;**[!UICONTROL Requisition List]**&#x200B;區段在每個Storefront頁面導覽中重新載入的問題，即使未進行任何變更亦然。

使用左側的功能表，導覽至特定的修補程式頁面。
