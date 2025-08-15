---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.55
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.55中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.55

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.55中可用修補程式所修正問題的詳細說明。

QPT v1.1.55包含下列修補程式：

1. **ACSD-58383**：修正透過[!DNL REST API]同時執行兩個相同要求而發出退款，會建立重複銷退折讓單的問題。
1. **ACSD-58471**：修正排程相關目錄價格規則時，無法在產品詳細資料頁面上載入動態內容的問題。
1. **ACSD-58566**：修正查詢[!DNL GraphQL]突變中的`created_at`欄位時，`addPurchaseOrderComment`傳回內部伺服器錯誤的問題。
1. **ACSD-58685**：修正當電子郵件通訊停用時啟動的銷售電子郵件在重新啟用電子郵件通訊後仍會傳送的問題。
1. **ACSD-58735**：修正受限制的管理員無法檢視相關網站[!UICONTROL Admin]中客戶帳戶頁面上的放棄購物車的問題。
1. **ACSD-58828**：修正伺服器端驗證訊息&#x200B;*位址為必要的問題*，若有任何必要欄位留空，此訊息會與使用者端驗證訊息一併顯示。 伺服器端驗證不會顯示空白必填欄位的訊息，而使用者端驗證將處理錯誤通知，指出&#x200B;*這是必填欄位。*
1. **ACSD-60344**：修正使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;自動核準時傳送重複訂單確認電子郵件的問題。
1. **ACSD-61348**：修正透過[!DNL GraphQL]顯示願望清單專案，但無法在多網站環境的店面中顯示的問題。
1. **ACSD-61534**：修正無法使用`bin/magento config:set`命令設定設計組態，且鎖定值可以透過表單操作進行變更的問題。 現在無法更新從[!DNL CLI]設定的`--lock-env`或`--lock-conf`鎖定值。
1. **ACSD-61785**：修正無法透過`reward_warning_notification`突變和[!DNL GraphQL]呼叫更新[!DNL REST API]屬性的問題，使其行為符合`reward_update_notification`。
1. **ACSD-62591**：修正設定&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;時主題未正確切換的問題。
1. **ACSD-62793**：修正匯出資料中`datetime`屬性不包含時間元件的問題。 此外，如果&#x200B;*[!UICONTROL Fields Enclosure]*&#x200B;已啟用&#x200B;**，則`additional_attributes`資料行中的屬性值會以雙引號括住。
1. **ACSD-62332**：修正產品清單[!DNL GraphQL]查詢僅限於10,000項產品中的`total_count`項的問題。 此外，修正透過[!DNL Live Search]查詢時，*在搜尋條件中將目前頁面設定為* 1 *，而非頁面* 2[!DNL GraphQL]的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
