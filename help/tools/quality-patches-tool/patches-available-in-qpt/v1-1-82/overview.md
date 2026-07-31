---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.82
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.82中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 9ea2dec8843119280f9ee291a89590024ddd2973
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.82

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.82中可用修補程式所修正問題的詳細說明。

QPT v1.1.82包含下列修補程式：

1. **ACP2E-4815**：修正記錄中造成PHP例外的多個GraphQL問題、修正透過GraphQL在訂購後建立的訂單與客戶帳戶之間的關聯，以及透過HTTP規格將回應與GraphQL保持一致。
1. **ACP2E-4194**：修正GraphQL回應針對無效、未授權或格式錯誤的請求傳回不正確HTTP狀態代碼的問題。
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)**：修正管理員使用者無法在管理員中使用&#x200B;**[!UICONTROL Add Products By SKU]**，將預設目錄中的產品新增至指定給未連結至共用目錄之客戶群組的公司的訂單的問題。
1. **ACP2E-4593**：修正多網站部署中，次要網站上針對網站限制顯示的CMS頁面不正確的問題。
1. **ACP2E-4682**：修正每次載入頁面時，造訪檢查報價單`isActive`狀態的Storefront頁面會建立空白報價記錄的問題。
1. **ACP2E-4695**：修正目錄規則索引器耗用過多記憶體且無法完成，導致不穩定及記憶體不足錯誤的問題。
1. **ACP2E-4698**：修正在「頁面產生器」文字內容中再次編輯影像時，會儲存絕對媒體URL，而非保留可攜式媒體指示詞的問題。
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**：修正獎勵點過期時間在含有大量獎勵點歷史記錄的商店中緩慢執行，造成獎勵點過期延遲的問題。
1. **ACP2E-4797**：修正即使資料庫設定為支援`utf8mb4`，在WYSIWYG編輯器或管理員的頁面產生器內容中輸入4位元組Unicode字元時仍遭到錯誤封鎖的問題。
1. **ACP2E-4799**：修正`requisition_lists` GraphQL查詢傳回`total_count`值的問題，該值僅反映目前頁面的專案數，而非符合查詢條件的請購單清單總數。
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**：修正清單中第一個可銷售子產品出現延遲時，含有許多子產品之可設定產品之簽出API要求顯著變慢的問題。
1. **ACP2E-4840**：修正`products` GraphQL查詢中要求的數量值傳回&#x200B;*null*&#x200B;的問題。
1. **ACP2E-4870**：修正&#x200B;**[!UICONTROL Product Alerts]**&#x200B;電子郵件通知忽略商店檢視電子郵件設定的問題。
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**：修正在「管理員」中檢視含大量通訊錄的客戶帳戶時，管理員使用者意外登出的問題。
1. **ACP2E-4894**：修正在大容量存放區啟用&#x200B;**[!UICONTROL Asynchronous Indexing]**&#x200B;時，新訂單在「管理訂單管理」格線中出現延遲的問題。
1. **ACP2E-4981**：修正頁面產生器產品輪播顯示產品的順序，未反映管理員中設定的位置，且在可設定產品時包含可設定產品且可個別顯示相符子產品的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
