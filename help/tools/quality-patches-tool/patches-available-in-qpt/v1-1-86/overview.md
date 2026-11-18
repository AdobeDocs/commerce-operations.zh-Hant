---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.86
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.86中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 95a2c8dc890366c96b6a8129e8ee25dd1b319190
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.86

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.86中可用修補程式所修正問題的詳細說明。

QPT v1.1.86包含下列修補程式：

1. **ACP2E-3094**：修正檢視或編輯具有許多許可權的類別的&#x200B;**[!UICONTROL Category Permissions]**&#x200B;時，可能導致瀏覽器無回應的問題。
1. **ACP2E-5046**：修正在Admin中建立訂單時，重新整理頁面多次新增相同SKU的問題。
1. **ACP2E-5050**：修正在Admin中檢視或儲存RMA時，**[!UICONTROL Action Logs]**&#x200B;報告中未顯示RMA號碼的問題。
1. **ACP2E-5057**：修正當&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;設為&#x200B;**[!UICONTROL Website]**&#x200B;時，套件組合產品的[!DNL GraphQL]查詢傳回全域套件組合選項價格而非網站特定價格的問題。
1. **ACP2E-5061**：修正類別銷售規則無法將`AND`條件與符合數個值之任一值的條件結合的問題。
1. **ACP2E-5071**：修正購物者的購物車已包含完整可用數量時，產品頁面上不一定會顯示庫存無法使用訊息的問題。
1. **ACP2E-5094**：修正設定`MAGENTO_DC_*`環境變數時頁面載入速度顯著變慢的問題。
1. **ACP2E-5118**：修正停用&#x200B;**[!UICONTROL Translations]**&#x200B;快取時，[!DNL Page Builder]預覽未呈現的問題。
1. **ACP2E-5134**：修正從公司的[!UICONTROL Shared Catalog]移除搭售方案的元件產品時，會讓搭售方案產品留在購物車中，造成購物車和結帳期間錯誤的問題。
1. **ACP2E-5146**：修正當其他網站上的客戶與管理員使用者具有相同的ID時，管理員使用者受限於特定網站無法刪除客戶的問題。
1. **ACP2E-5176**：修正透過[!DNL Google Tag Manager]傳送至[!DNL Google Analytics 4]的電子商務事件使用[!DNL Universal Analytics]格式並忽略數個結帳事件的問題。
1. **ACP2E-5185**：修正移動類別樹狀結構中的類別時顯示錯誤`There was a category move error`的問題，或當存放區有多個URL重寫時，需要幾分鐘才能完成。
1. **ACP2E-4191**：修正停用&#x200B;**[!UICONTROL EAV types and attributes]**&#x200B;快取時，特定REST API要求進入無限回圈的問題。
1. **ACP2E-4973**：修正從&#x200B;**[!UICONTROL In-Store Delivery]**&#x200B;切換至其他傳遞方式時，無法從購物車中清除相關商店位址的問題。
1. **ACP2E-5221**：修正在多個商店和客戶群組的安裝中啟用&#x200B;**[!UICONTROL Quick Order]**&#x200B;時，**[!UICONTROL Catalog Product Permissions]**&#x200B;索引子需要更長時間的問題。
1. **ACP2E-5245**：修正新註冊客戶第一次訂購時使用相同地址進行運送和帳單時，在下次結帳期間看到該地址列示兩次的問題。
1. **ACP2E-5248**：修正在[!DNL PHP] 8.5上開啟&#x200B;**[!UICONTROL Add Product]**&#x200B;頁面時，沒有&#x200B;**[!UICONTROL Edit Product Status]**&#x200B;許可權的管理員使用者會看到`null as array offset`棄用錯誤的問題。
1. **ACP2E-5254**：修正當客戶開啟請購單清單，直到快取清除為止，產品未顯示的問題。
1. **ACP2E-5268**：修正當&#x200B;**[!UICONTROL Enable Frontend Resize]**&#x200B;設為&#x200B;**[!UICONTROL No]**&#x200B;時，建立可設定產品失敗的問題。
1. **ACP2E-3752**：修正建立許多產品匯入作業時，產品匯入處理擲回錯誤`Undefined array key "apply_to"`的問題。
1. **ACP2E-5280**：修正啟用&#x200B;**[!UICONTROL Category Permissions]**&#x200B;時，客戶在登入時遇到錯誤的問題。
1. **ACP2E-5295**：修正平行產品價格重新索引在同一個處理程式中的&#x200B;**[!UICONTROL Inventory]**&#x200B;索引器之後執行時失敗，並出現錯誤`Fail in child process`的問題。
1. **ACP2E-5298**：修正對購物車價格規則具有僅限檢視存取權的管理員使用者可以產生或刪除優惠券代碼的問題。
1. **ACP2E-5333**：修正重新整理客戶區段的問題，該客戶區段的&#x200B;**[!UICONTROL Total Number of Orders]**&#x200B;條件使用&#x200B;**[!UICONTROL is not]**&#x200B;運運算元，且一或多個值失敗，並出現錯誤`Unknown operator specified`。
1. **ACP2E-5425**：修正客戶收到相同訂單的重複訂單確認電子郵件的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
