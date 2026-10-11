---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.31
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.31中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.31

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.31中可用修補程式所修正問題的詳細說明。

QPT v1.1.31包含下列修補程式：

1. **ACSD-50817**：透過在引號資料表的`store_id`和`updated_at`資料行上新增複合索引，將cron工作`sales_clean_quotes`最佳化以更快地執行。
1. **ACSD-50345**：修正下列問題： [!DNL Google reCAPTCHA v2]在提交失敗的付款後未重新載入、[!DNL Google reCAPTCHA v3 Invisible]無法正常結帳，且無法下訂單，以及未觸發[!UICONTROL PlaceOrder]事件。
1. **ACSD-49392**：修正套件產品部分退款後，訂單狀態變更為已關閉的問題。
1. **ACSD-51036**：修正同時REST API呼叫期間的競爭條件導致[!UICONTROL Items Ordered]表格中出貨狀態資訊覆寫的問題。
1. **ACSD-50858**：修正信用卡付款失敗後，優惠券被錯誤地標示為使用的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
