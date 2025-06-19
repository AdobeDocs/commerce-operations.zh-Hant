---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.58
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.58中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.58

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.58中可用修補程式所修正問題的詳細說明。

QPT v1.1.58包含下列修補程式：

1. **ACSD-48570**：修正當&#x200B;**將市集代碼新增至URL**&#x200B;已啟用&#x200B;*時，無法透過按一下[!UICONTROL Admin]重設密碼連結來存取重設密碼頁面的問題*，此問題之前會導致登入頁面或顯示404頁面。
1. **ACSD-62118**：修正使用「採購單」方法下達[!DNL B2B]份訂單時，`sales_order_tax_item`資料表未完全更新的問題。
1. **ACSD-63067**：修正所有產品數量都未正確標示的問題，而且當只有一個數量不正確時，會針對分組產品中的所有產品顯示訊息&#x200B;*[!DNL Please specify the quantity of product(s).]*。
1. **ACSD-63090**：修正將產品加入購物車後，當產品被刪除時購物車專案被移除的問題。
1. **ACSD-63182**：修正儲存重複套件組合產品並啟用&#x200B;**[!DNL MSI]** *時發生錯誤的問題*。
1. **ACSD-63283**：修正從禮品登入訂購專案時發生例外狀況，以及禮品登入更新包含不屬於登入的專案的問題。
1. **ACSD-63299**：修正店面未顯示可設定產品特殊價格的問題。
1. **ACSD-63325**：修正提交空的[!DNL GraphQL]請求時發生`Syntax Error: Unexpected <EOF>`錯誤的問題。
1. **ACSD-63329**：修正透過[!DNL REST API]建立產品時，具有&#x200B;**[!UICONTROL Date]**&#x200B;或&#x200B;**[!UICONTROL Date and Time]**&#x200B;輸入型別的屬性預設值未設定的問題。
1. **ACSD-63572**：修正索引器處理序終止時，`CatalogRule`索引器暫存資料表未清除的問題。
1. **ACSD-63578**：修正在[!UICONTROL Admin]中按一下&#x200B;**[!UICONTROL Add to Order by SKU]**&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;按鈕未移除[!DNL SKU]的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
