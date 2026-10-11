---
title: ACSD-62635： [!DNL GraphQL]中無法正確顯示多商店相關產品
description: 套用ACSD-62635修補程式以修正Adobe Commerce問題，多商店相關產品未正確顯示在[!DNL GraphQL]產品查詢中。
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-62635： [!DNL GraphQL]中無法正確顯示多商店相關產品

ACSD-62635修補程式修正多商店相關產品未在[!DNL GraphQL]產品查詢中正確顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62635。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用B2B時，即使要求中使用商店檢視範圍，[!DNL GraphQL]要求也會傳回所有網站的所有相關產品。

<u>要再現的步驟</u>：

1. 建立兩個網站、商店和商店檢視。
1. 建立下列簡單產品：
   * 一個主要SKU為&#x200B;*product1*&#x200B;的已指派給所有網站
   * 一個僅指派給&#x200B;*網站1*
   * 僅指派給&#x200B;*網站2*&#x200B;的一個
   * 一個已指派給&#x200B;*網站1*&#x200B;和&#x200B;*網站2*
1. 新增與&#x200B;*product1*&#x200B;相關的所有產品。
1. 啟用[!UICONTROL B2B]和[!UICONTROL Shared Catalog]。
1. 將所有產品新增至預設的共用目錄。
1. 傳送[!DNL GraphQL]要求以擷取&#x200B;*product1*&#x200B;及其相關產品，標題中的商店代碼為&#x200B;*網站1*。

<u>預期結果</u>：

回應僅包含來自網站的相關產品，這些產品對應至要求標頭中傳送的商店代碼。

<u>實際結果</u>：

回應包含所有網站的所有相關產品，無論請求中指定的商店程式碼為何。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
