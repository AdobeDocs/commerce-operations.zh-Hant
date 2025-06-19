---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.54
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.54中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.54

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.54中可用修補程式所修正問題的詳細說明。

QPT v1.1.54包含下列修補程式：

1. **ACSD-60267**：修正當直接將具有FPT的簡單產品新增至購物車時，Fixed Product Tax (FPT)會正確套用的問題，但在透過可設定的產品選項選取這些產品時失敗。
1. **ACSD-61103**：修正客戶透過API端點成功登入後，`customer_entity`表格中的失敗計數未重設為零的問題。
1. **ACSD-61134**：修正當購物者取消選取&#x200B;*[!UICONTROL My billing and shipping address are the same]*&#x200B;核取方塊以更新其帳單地址時，在結帳工作流程中自動取消選取[!DNL Braintree Vault]付款方式的問題。
1. **ACSD-61199**：修正CMS頁面階層索引標籤在編輯具有現有階層的CMS頁面時未顯示正確樹狀結構的問題。
1. **ACSD-61200**：修正銷售中&#x200B;*[!UICONTROL Total Amount]*&#x200B;與&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;的計算遺失&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;與&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，造成銷售訂單資料不一致的問題。
1. **ACSD-61522**：修正可能將電子郵件地址輸入客體客戶的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;欄位，並傳送無效訂單確認電子郵件的問題。
1. **ACSD-61756**：改善`AdvancedSalesRule`篩選器的效能。
1. **ACSD-61799**：修正當多個具有固定折扣的購物車規則套用至報價時，總折扣計算錯誤的問題。
1. **ACSD-61845**：修正只傳送&#x200B;*text/html*&#x200B;接受標頭的請求時發生的錯誤。
1. **ACSD-62056**：修正安裝MSI時可設定產品影像上傳失敗的問題。
1. **ACSD-62485**：修正`async.operations.all`消費者在建立公司時停止運作的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
