---
title: '概觀： [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.42中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.42

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.42中可用修補程式所修正問題的詳細說明。

QPT v1.1.42包含下列修補程式：

1. **ACSD-53658**：修正商店檢視中&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;產品資料未正確更新的問題。
1. **ACSD-54626**：修正無法透過GraphQL建立具有`NUMBER_OF_SKUS`屬性的新採購單規則(`createPurchaseOrderApprovalRule`)的問題。
1. **ACSD-53845**：修正`consumer max_messages` = 0時的MySQL連線逾時問題。
1. **ACSD-54890**：修正`aggregate_sales_report_bestsellers_data`由於`/tmp`磁碟空間不足而導致MySQL錯誤的問題。
1. **ACSD-55112**：修正可多次點選「*[!UICONTROL Submit review]*」按鈕而無需[!DNL Google reCAPTCHA v3]驗證的問題。
1. **ACSD-54264**：修正錯誤訊息&#x200B;*您無法更新要求的屬性的問題。 資料列識別碼：當客戶嘗試從另一個商店檢視使用可轉讓的報價結帳時，就會出現store_id*。
1. **ACSD-54418**：修正動態定價套件組合的每個子產品不正確套用固定金額折扣的問題。
1. **ACSD-55238**：修正儲存空白產品中繼描述的問題。
1. **ACSD-54966**：修正先前訂單失敗時，無法重新使用每位客戶有限使用優惠券代碼的問題。
1. **ACSD-54060**：修正受限管理員無法儲存產品（若為指派給不同範圍之其他產品的子項）的問題。
1. **ACSD-48910**：修正訂單開立商業發票及出貨後，即使數量非零，指定給多個來源的套件產品也會缺貨的問題。
1. **ACSD-55381**：修正透過GraphQL從B2B *[!UICONTROL Requisition list]*&#x200B;查詢`configurable_product_option_uid`和`configurable_product_option_value_uid`欄位時的內部伺服器錯誤。
1. **ACSD-55628**：修正上傳公司登錄檔單上的檔案，並取代店面中客戶屬性的檔案。

使用左側的功能表，導覽至特定的修補程式頁面。
