---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.72
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.72中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 89b78f72fce3f65b8f282038cc4e2ef0f190bda3
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.72

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.72中可用修補程式所修正問題的詳細說明。

QPT v1.1.72包含下列修補程式：
1. **ACSD-68040**：前端搜尋頁面在[!DNL MariaDB] 10.6和11.4上出現效能降低的情況，並有許多歷史搜尋要求。
1. **ACSD-67941**：具有未知篩選名稱的GraphQL要求會造成PHP例外狀況記錄檔。
1. **ACSD-68064**：建立排程的更新會在含有大量巢狀類別的環境中造成重複專案。
1. **ACSD-66807**： `report_viewed_product_index`表格顯示不正確的產品頁面檢視計數。
1. **ACSD-67383**：以客戶身分登入時，若在同一個工作階段中有兩個公司管理員帳戶，會導致&#x200B;*沒有此類實體出現cartId*&#x200B;錯誤。
1. **ACSD-67518**：進階報表在資料列計數超過批次大小時產生重複的標題資料列。
1. **ACSD-67639**：為&#x200B;**[!UICONTROL Dynamic Price]**&#x200B;設為&#x200B;*No*&#x200B;的套件組合產品建立銷退折讓單失敗。
1. **ACSD-67696**：快取排清後，`media_gallery`專案沒有傳回購物車GraphQL產品節點。
1. **ACSD-67946**：購物車更新顯示重複的錯誤橫幅。
1. **ACSD-68011**：可以透過`/V1/sharedCatalog/:id/assignProducts` [!DNL REST] API將不存在的SKU指派給共用目錄。
1. **ACSD-68118**： `customerCart` GraphQL查詢傳回的產品屬性值未反映商店標題，導致本地化不一致。
1. **ACSD-68092**：由於排定的更新與基本產品資料之間的同步處理錯誤，多次儲存後套裝產品選項會遺失。
1. **ACSD-67424**： `updated_at` `GET /carts/search` API回應中的[!DNL REST]值與使用可轉讓引號時&#x200B;**[!UICONTROL Admin panel]**&#x200B;中顯示的值不符。
1. **ACSD-67187**：限制在非預設網站的管理員使用者看見錯誤，*「*」請至少建立公開共用目錄以繼續*，並且無法存取公司格線上的&#x200B;**[!UICONTROL Add New Company]**&#x200B;按鈕。

使用左側的功能表，導覽至特定的修補程式頁面。
