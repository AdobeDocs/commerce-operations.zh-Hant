---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.35
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.35中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin
exl-id: 5ffbade4-c95e-4b59-9262-1b141614c753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.35

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.35中可用修補程式所修正問題的詳細說明。

QPT v1.1.35包含下列修補程式：

1. **ACSD-51899**：修正結帳出貨步驟上的預設出貨地址自動填入先前選取的店內取貨地址的問題。
1. **ACSD-52041**：修正錯誤訊息： *[錯誤] [!DNL Page Builder]呈現5秒而未解除鎖定*&#x200B;的問題。 儲存使用[!DNL Chrome]編輯的內容時在[!DNL Page Builder]瀏覽器中顯示。
1. **ACSD-52095**：修正產品匯出後，CSV檔案中的`manage_stock`值未正確設為0的問題。
1. **ACSD-51358**：修正移除沒有結束日期的排程更新會導致移除相同實體的其他排程更新的問題。
1. **ACSD-48070**：修正編輯排程更新時觸發例外狀況的問題。
1. **ACSD-51890**：修正可多次點選「[!UICONTROL Submit review]」按鈕而無[!DNL Google] reCAPTCHA v3驗證的問題。
1. **ACSD-51984**：修正未勾選的問題&#x200B;*使用預設值及非預設產品欄位值*&#x200B;無法儲存第二個網站、商店及商店檢視。
1. **ACSD-52398**：修正錯誤&#x200B;*要求的數量無法使用*，此錯誤發生在嘗試更新店面購物車中捆綁產品的數量時。
1. **ACSD-52786**：修正從指定SKU開始將目錄規則條件SKU套用至所有產品的問題。
1. **ACSD-52921**：修正當購物車有無庫存的可設定產品時，從GraphQL要求購物車詳細資料時發生內部錯誤的問題。
1. **ACSD-51683**：修正無法使用GraphQL將可自訂選項新增到購物車的問題。
1. **ACSD-52133**：修正升級後無法儲存客戶帳戶的問題。
1. **ACSD-52202**：修正訂單履行時，非預設存貨變更為0數量時，預設存貨的可銷售數量錯誤地變更為0的問題。
1. **ACSD-51265**：修正系統中有太多隨附產品時，`catalog_product_price`重新索引效能的問題。
1. **ACSD-52831**：修正啟用[!DNL Google reCAPTCHA v3 Invisible]時，客戶無法下可轉讓報價單的問題。
1. **ACSD-51845**：修正無法透過非同步大量REST API更新含有階層價格及不同屬性集的後續產品的問題。
1. **ACSD-52815**：修正非預設來源之數量欄位輸入最多只支援6位數（預設庫存則支援8位數）的問題。
1. **ACSD-51149**：修正啟用[!UICONTROL Scheduled ImportExport]的[!UICONTROL Catalog Permissions]使索引子失效，然後由cron快取排清的問題。
1. **ACSD-50815**：修正簡單產品的小數點數量無法用於新捆綁產品選項的問題。
1. **ACSD-52399**：修正可銷售數量為0的可設定產品選項在產品頁面上顯示&#x200B;*庫存*&#x200B;的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
