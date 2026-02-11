---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.75
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.75中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: d952deb1c82ce0d99c3e13909cfc18b7a48034c3
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.75

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.75中可用修補程式所修正問題的詳細說明。

QPT v1.1.75包含下列修補程式：
1. **ACSD-68289**：修正如果所有可搜尋欄位整體符合最低符合條件，全文檢索搜尋現在會傳回符合產品的問題，而不是要求條件必須由單一欄位符合的問題。
1. **ACSD-68359**：修正使用&#x200B;**[!UICONTROL Pick in Store]**&#x200B;在結帳時選取商店的問題，此問題不再因為購物車中有許多產品時URL過長而失敗。 之前，這會在商店銷售期間產生過長的URL，因而觸發414錯誤。
1. **ACSD-68451**：修正多個網站的問題，其中公司管理員登入一個網站，在另一個網站上建立不相關的公司，但錯誤地連結到該不相關的公司。
1. **ACSD-68490**：受限制的管理員在可設定產品建立期間可看到&#x200B;**[!UICONTROL Add New Attribute]**&#x200B;按鈕。
1. **ACSD-68517**：修正目錄和目錄搜尋頁面上的表單重新提交錯誤。
1. **ACSD-68573**：修正類別許可權未正確套用至客戶願望清單專案的問題。 修正後，願望清單專案可在網頁和GraphQL中正確顯示和分頁。
1. **ACSD-68615**：修正當處理的組合遺失訂單識別碼時，存貨預留補償CLI顯示例外狀況的問題。
1. **ACSD-68793**：修正將有效產品指派至共用目錄時，無法正確拒絕有效產品的問題。
1. **ACSD-68925**：修正GraphQL要求的回應現在透過HTTP規格與GraphQL對齊的問題。 當請求無法剖析、未獲授權或遇到一般問題（如果請求已剖析）時，會傳回4XX回應代碼。

使用左側的功能表，導覽至特定的修補程式頁面。
