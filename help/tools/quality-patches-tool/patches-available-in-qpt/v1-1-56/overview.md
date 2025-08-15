---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.56
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.56中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.56

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.56中可用修補程式所修正問題的詳細說明。

QPT v1.1.56包含下列修補程式：

1. **ACSD-63244**：修正JavaScript錯誤導致[!DNL Google Maps]無法正確轉譯，以及有多個&#x200B;*Uncaught TypeError的問題：這個。_each不是*&#x200B;面板中主控台中的函式[!UICONTROL Admin]錯誤。
1. **ACSD-63242**：修正新增包含超過10,000個專案的目錄產品時，匯入速度緩慢的問題。
1. **ACSD-63062**：修正套用多個重疊規則時，發生不正確購物車折扣計算的問題。
1. **ACSD-62979**：修正在GraphQL標頭中使用錯誤[!UICONTROL Store ID]導致嚴重記憶體錯誤的問題。
1. **ACSD-62971**：修正匯入&#x200B;*[!UICONTROL Quantity]*&#x200B;欄中有非數值的庫存來源時，*數量*&#x200B;設為&#x200B;*0*&#x200B;的問題。
1. **ACSD-62872**：修正唯一屬性驗證時未正確驗證排程更新的問題。
1. **ACSD-62755**：修正[!DNL TinyMCE] 7需要在編輯器初始化設定中特別新增字型大小和字型的問題。
1. **ACSD-62670**：修正[!UICONTROL Products Ordered]報告匯出為CSV和XML時傳回錯誤的問題。
1. **ACSD-62577**：透過最佳化查詢和資料表索引，修正店面搜尋查詢效能緩慢的問題。
1. **ACSD-62475**：修正購物車中[!UICONTROL Gift Card]產品不正確合併的問題。
1. **ACSD-62428**：修正當`is_out_of_stock`未設定為可搜尋的屬性時，[!DNL SKU]在目錄搜尋索引中設定為不正確值的問題。
1. **ACSD-62355**：當可設定產品是以許多具有許多值的許多屬性為基礎時，可改善可設定產品編輯頁面的載入時間。
1. **ACSD-61805**：修正透過[!DNL REST API]更新延期交貨狀態後，店面產品無存貨的問題。
1. **ACSD-60811**：修正目前狀態為&#x200B;*[!UICONTROL Processing]*&#x200B;或&#x200B;*[!UICONTROL Fraud]*&#x200B;時，才可使用自訂值或註解來更新訂單狀態的問題。
1. **ACSD-62952**：修正店面未正確顯示[!UICONTROL Gift Registry]日期的問題。
1. **ACSD-55339**：修正以[!DNL SKU]0 *（零）開頭的產品*&#x200B;移除&#x200B;*0*，導致報價無法更新的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
