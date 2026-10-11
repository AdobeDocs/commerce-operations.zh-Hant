---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.53
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.53中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '243'
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
