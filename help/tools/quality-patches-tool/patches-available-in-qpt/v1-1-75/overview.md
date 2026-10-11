---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.75
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.75中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '267'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.75

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.75中可用修補程式所修正問題的詳細說明。

QPT v1.1.75包含下列修補程式：
1. **ACSD-68289**：修正如果所有可搜尋欄位整體符合最低符合條件，全文檢索搜尋現在會傳回符合產品的問題，而不是要求條件必須由單一欄位符合的問題。
1. **ACSD-68359**：選取大型購物車的&#x200B;**[!UICONTROL Pick in Store]**&#x200B;時，修正&#x200B;*414*&#x200B;錯誤。
1. **ACSD-68451**：修正多個網站的問題，其中公司管理員登入一個網站，在另一個網站上建立不相關的公司，但錯誤地連結到該不相關的公司。
1. **ACSD-68517**：修正&#x200B;**[!UICONTROL Catalog]**&#x200B;和&#x200B;**[!UICONTROL Catalog Search]**&#x200B;頁面上的表單重新提交錯誤。
1. **ACSD-68490**：受限制的管理員在可設定產品建立期間可看到&#x200B;**[!UICONTROL Add New Attribute]**&#x200B;按鈕。
1. **ACSD-68573**：類別許可權未套用至客戶願望清單專案，導致網頁店面和[!DNL GraphQL]中的顯示和分頁不正確。
1. **ACSD-68615**：修正當處理的組合遺失訂單識別碼時，存貨預留補償CLI顯示例外狀況的問題。
1. **ACSD-68793**：修正將有效產品指派至共用目錄時，無法正確拒絕有效產品的問題。
1. **ACSD-68925**：修正GraphQL要求的回應現在透過HTTP規格與GraphQL對齊的問題。 當請求無法剖析、未獲授權或遇到一般問題（如果請求已剖析）時，會傳回4XX回應代碼。

使用左側的功能表，導覽至特定的修補程式頁面。
