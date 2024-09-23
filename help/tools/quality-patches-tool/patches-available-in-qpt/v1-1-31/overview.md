---
title: '概觀： [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.31中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '171'
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
