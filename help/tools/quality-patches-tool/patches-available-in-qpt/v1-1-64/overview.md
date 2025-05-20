---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.64
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.64中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.64

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.64中可用修補程式所修正問題的詳細說明。

QPT v1.1.64包含下列修補程式：

1. **ACP2E-3838**：修正[!DNL Page Builder] CORS錯誤導致無法在生產模式中儲存管理面板中的變更的問題。
1. **ACP2E-3841**：修正使用`subselect`個條件且啟用&#x200B;**[!UICONTROL Free Shipping]**&#x200B;時，多送貨產品的購物車價格規則無法正確套用的問題。
1. **ACSD-63139**：修正產品屬性包含數千個選項值時產品匯出失敗的問題。
1. **ACSD-65100**：修正移除&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;組態中&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;的值在影像最佳化程式期間導致錯誤的問題。
1. **ACSD-65127**：修正在生產模式中啟用JavaScript縮制導致[!DNL TinyMCE] 6在瀏覽器主控台中產生錯誤，影響功能和使用者體驗的問題。
1. **ACSD-65787**：修正當處理資料表資料時，`SchemaBuilder`類別會在結構描述建立或更新期間因未定義的陣列索引鍵&#x200B;*column*&#x200B;而當機的問題。
1. **ACSD-65223**：修正手動選取[!DNL B2B]份採購單之條款與合約導致錯誤的問題。
1. **ACSD-65540**：修正更新`company_structure`資料表時，因缺少`REGEXP_LIKE`函式而發生SQL語法錯誤的問題。
1. **ACSD-65684**：修正在`company_structure`表格中處理大量記錄(~100,000+)時，更新至[!DNL B2B] 1.5.2後升級`Magento_Company`模組所花費的時間過長的效能問題。

使用左側的功能表，導覽至特定的修補程式頁面。
