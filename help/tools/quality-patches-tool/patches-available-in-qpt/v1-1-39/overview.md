---
title: '概觀： [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.39中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.39

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.39中可用修補程式所修正問題的詳細說明。

QPT v1.1.39包含下列修補程式：

1. **ACSD-53704**：修正獎勵點到期後獎勵點餘額歷史記錄計算錯誤的問題。
1. **ACSD-53583**：改善&#x200B;*類別產品*&#x200B;和&#x200B;*產品類別*&#x200B;索引器的部分重新索引效能。
1. **ACSD-54026**：修正非授權使用者`updateCompanyRole` GraphQL要求的錯誤訊息。
1. **ACSD-54106**：修正按名稱排序土耳其文重音字元的產品不正確的問題。
1. **ACSD-52219**：修正經常在書籤檢視之間切換時，管理員格線儲存的篩選器無法如預期運作的問題。
1. **ACSD-54342**：修正錯誤的錯誤訊息&#x200B;*資料結構中的錯誤：匯入沒有有效資料的CSV檔案時，會混合值*。
1. **ACSD-54660**：已新增輸入屬性&#x200B;*sort*，以便在GraphQL中依`sort_field`與`sort_direction`排序客戶訂單。
1. **ACSD-54776**：修正未核取的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;以及未儲存第二個網站、商店和商店檢視的非預設產品欄位值的問題。
1. **ACSD-53998**：修正從客戶帳戶登出後，以&#x200B;**[!UICONTROL Customer Segment]**&#x200B;為基礎的&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;無法正常運作的問題。
1. **ACSD-53204**：修正&#x200B;*無法儲存產品。使用`rest/V1/products/<sku>/media`端點同時要求將影像新增至產品相簿時發生*&#x200B;錯誤。
1. **ACSD-47657**：已新增AWS憑證的快取機制。 認證提供者現在會使用Magento快取來快取從AWS擷取的認證，以進行EC2設定。

使用左側的功能表，導覽至特定的修補程式頁面。
