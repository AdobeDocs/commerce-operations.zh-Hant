---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.53
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.53中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.53

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.53中可用修補程式所修正問題的詳細說明。

QPT v1.1.53包含下列修補程式：

1. **ACSD-48318**：修正不允許環境模擬巢狀的問題。 現在，模擬會在`send()`呼叫期間啟動，一旦模擬在`getInfoBlockHtml()`呼叫期間停止。
1. **ACSD-59930**：改善公司&#x200B;*[!UICONTROL Create]*、*[!UICONTROL Save]*&#x200B;和&#x200B;*[!UICONTROL Delete]*&#x200B;流程的效能。
1. **ACSD-60584**：修正一個網站上為使用者建立的存取Token可存取或變更其他網站上的客戶資訊的問題。
1. **ACSD-60804**：修正編輯連結至已刪除公司的客戶造成錯誤&#x200B;*呼叫null*&#x200B;上的成員函式`getSuperUserId()`的問題。
1. **ACSD-61133**：修正`sales_clean_quotes` cron從未核准的採購單刪除報價的問題。
1. **ACSD-61528**：修正使用GraphQL從[!UICONTROL Admin]擷取角色時未傳回任何結果的問題。
1. **ACSD-61553**：修正將具有不同優先順序和&#x200B;*[!UICONTROL Maximum Qty Discount is Applied To]*&#x200B;的多個折扣套用至產品時，*[!UICONTROL Cart Price Rule]*&#x200B;個折扣計算錯誤的問題。
1. **ACSD-61667**：改善存貨效能，以建立多個有&#x200B;*店內取貨*&#x200B;之來源的送貨。
1. **ACSD-61969**：修正使用者必須輸入與設定之優惠券代碼完全相符且區分大小寫的優惠券代碼的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
