---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.48
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.48中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.48

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.48中可用修補程式所修正問題的詳細說明。

QPT v1.1.48包含下列修補程式：

1. **ACSD-55566**：修正當合併來源和目的地購物車具有相同的整合專案時，*[!UICONTROL mergeCart mutation]*&#x200B;在GraphQL回應中失敗並出現&#x200B;*內部伺服器錯誤*&#x200B;的問題。
1. **ACSD-56546**：修正停用&#x200B;*[!UICONTROL Display Out of Stock Product]*&#x200B;設定時，可設定和隨附的產品在店面顯示為&#x200B;*[!UICONTROL Out of Stock]*&#x200B;的問題。
1. **ACSD-56635**：修正當匯入用於[!UICONTROL Account Sharing]設為&#x200B;*[!UICONTROL Global]*&#x200B;時，匯入的客戶重複使用相同電子郵件地址的問題。
1. **ACSD-56741**：修正錯誤訊息&#x200B;*當資料庫包含與索引機制和[!DNL MView]無關的自訂MySQL觸發程式時，嘗試存取在`setup:upgrade`期間顯示的null型別*&#x200B;值的陣列位移。
1. **ACSD-57315**：修正每次在[!UICONTROL Admin]的檢視交易畫面上按一下&#x200B;**[!UICONTROL Fetch]**&#x200B;按鈕時，[!DNL PayPal Payflow Pro]中都會建立新交易的問題。
1. **ACSD-57337**：修正具有特定網站存取限制的管理員使用者可看到&#x200B;*[!UICONTROL Companies]*&#x200B;格線中所有網站的公司的問題。
1. **ACSD-57394**：修正GraphQL中依多個排序欄位排序的產品不正確問題。
1. **ACSD-57565**：修正&#x200B;*[!UICONTROL Order]*&#x200B;儀表板在更新時段之前顯示錯誤訂單資訊的問題。 儀表板現在會在首次載入時顯示正確的訂單統計資料。
1. **ACSD-57854**：修正產品GraphQL請求在類別彙總中傳回停用類別的問題。
1. **ACSD-58008**：修正在未指定結束日期時，更新排定的更新會移除分段專案的先前版本的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
