---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.85
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.85中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: 4d61208c23f1d1fe38664a838149ba51958eddac
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.85

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.85中可用修補程式所修正問題的詳細說明。

QPT v1.1.85包含下列修補程式：

1. **ACP2E-4929**：修正&#x200B;**[!UICONTROL Compare Products]**&#x200B;頁面上的屬性標籤顯示不同商店檢視（而非目前商店檢視）的翻譯的問題。
1. **ACP2E-5075**：修正固定金額購物車價格規則與類別條件不正確套用折扣（當規則僅符合搭售組合父項產品時）至動態價格搭售組合產品所有子項的問題。
1. **ACP2E-5077**：修正並行的`customerCart`個GraphQL查詢或`POST /V1/carts/mine`個REST要求為尚未擁有作用中購物車的客戶建立重複作用中購物車的問題。
1. **ACP2E-5088**：修正工作階段過期時客戶永久購物車被清除的問題。
1. **ACP2E-3991**：修正使用者端IP位址未正確判斷的問題。
1. **ACP2E-5092**：修正&#x200B;**[!UICONTROL Company Profile]**&#x200B;頁面和管理員客戶編輯頁面在儲存的公司地址之後沒有區域時，在國家/地區新增區域時顯示錯誤的問題。
1. **ACP2E-5124**：修正當&#x200B;**[!UICONTROL Validation Strategy]**&#x200B;設為&#x200B;**[!UICONTROL Stop on Error]**&#x200B;時，驗證失敗後，**[!UICONTROL Import]**&#x200B;按鈕在驗證結果中仍然可用的問題。
1. **AC-17456**：修正在Admin Panel的&#x200B;**[!UICONTROL Design Configuration]**&#x200B;頁面上編輯&#x200B;**[!UICONTROL Global]**&#x200B;範圍時，在PHP 8.4和8.5上傳回&#x200B;*HTTP 500*&#x200B;錯誤的問題。
1. **ACP2E-5212**：修正&#x200B;**[!UICONTROL Quick Order]**&#x200B;接受副檔名為`.csv`的非CSV檔案的問題。
1. **ACP2E-5300**：修正關鍵字在管理面板&#x200B;**[!UICONTROL Orders]**&#x200B;格線中搜尋多個以空格或逗號分隔的訂單編號時，未傳回任何相符訂單的問題。
1. **ACP2E-5354**：修正透過REST API更新客戶時，與公司帳戶相關聯的客戶會在Admin **[!UICONTROL Customers]**&#x200B;格線中出現多次的問題。
1. **ACP2E-5208**：修正&#x200B;**[!UICONTROL Requisition List]**&#x200B;區段在每個Storefront頁面導覽中重新載入的問題，即使未進行任何變更亦然。

使用左側的功能表，導覽至特定的修補程式頁面。
