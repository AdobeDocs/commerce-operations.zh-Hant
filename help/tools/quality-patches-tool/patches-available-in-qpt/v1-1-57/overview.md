---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.57
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.57中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.57

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.57中可用修補程式所修正問題的詳細說明。

QPT v1.1.57包含下列修補程式：

1. **ACSD-57570**：修正具有特定商店存取權的受限管理員使用者無法一律看見產品所指派的所有共用目錄，或無法看見客戶儲存，導致系統不一致的問題。
1. **ACSD-58325**：修正[!UICONTROL Import]按鈕在驗證錯誤後仍可用的問題。
1. **ACSD-59083**：修正某些資料庫更新作業導致&#x200B;_找不到基底資料表或檢視的問題_&#x200B;錯誤（如果[!DNL mview]更新同時執行）。
1. **ACSD-61622**：修正回應中缺少[!DNL FedEx]帳戶特定費率的問題。 ACSD-61622取代[[!DNL FedEx] 送貨方法整合從 [!DNL SOAP] 移轉至 [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api)中記錄的修正。
1. **ACSD-61895**：修正即使根類別沒有&#x200B;*允許*&#x200B;許可權，類別[!DNL GraphQL]查詢傳回具有&#x200B;*允許*&#x200B;許可權的類別的問題。
1. **ACSD-62212**：修正[!UICONTROL Forgot Password]電子郵件內容未翻譯成商店檢視語言的問題。
1. **ACSD-62481**：修正即使啟用[!UICONTROL Persistence]，客戶的購物車還是空白的問題。
1. **ACSD-62629**：修正[!UICONTROL Widgets]中使用的產品清單未遵守類別條件的問題。
1. **ACSD-62635**：修正[!DNL GraphQL]產品查詢中無法正確顯示多商店相關產品的問題。
1. **ACSD-62671**：修正[!DNL GraphQL]請求在第一次嘗試時未傳回最新位址資訊的問題。
1. **ACSD-62689**：修正客戶無法在深度4後新增[!UICONTROL Related Product Rules]和[!UICONTROL Widgets]中的類別的問題。
1. **ACSD-62708**：修正套用[!UICONTROL ACP2E-3430]的修正後，管理員中的[!DNL TinyMCE] 7編輯器字型大小顯示[!UICONTROL pt]而非[!UICONTROL px]的問題。 現在，您也可以在[!UICONTROL px]中設定字型大小，而非[!UICONTROL pt]。
1. **ACSD-62758**：修正URL包含選取的選項時，[!UICONTROL Configurable Product]詳細資料頁面上的產品影片無法正確轉譯的問題。
1. **ACSD-62951**：修正傳送[!UICONTROL Credit Memo]電子郵件時不含專案和總計的問題。
1. **ACSD-62965**：修正訂單位置[!DNL GraphQL response]中未包含&#x200B;*LocalizedException*&#x200B;訊息的問題。
1. **ACSD-63286**：修正手動重新索引執行前，透過API指派給共用目錄的產品未出現在店面的問題。
1. **ACSD-63326**：修正從後端下訂單後，將管理員重新導向至中斷頁面的問題。


使用左側的功能表，導覽至特定的修補程式頁面。
