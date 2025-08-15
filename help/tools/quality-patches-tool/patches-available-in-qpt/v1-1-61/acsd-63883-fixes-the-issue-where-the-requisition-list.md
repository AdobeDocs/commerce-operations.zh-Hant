---
title: ACSD-63883：修正 [!DNL GraphQL] 在[!UICONTROL Requisition List]回應中錯誤的「items_count」
description: 套用ACSD-63883修補程式以修正[!UICONTROL Requisition List]回應中 [!DNL GraphQL] 傳回不正確「items_count」的問題。
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883：修正`items_count`在[!DNL GraphQL]回應中錯誤的[!UICONTROL Requisition List]

ACSD-63883修補程式修正&#x200B;**[!UICONTROL Requisition List]**&#x200B;回應中`items_count`傳回不正確[!DNL GraphQL]的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-63883。 請注意，此問題已排程在Adobe Commerce B2B 1.5.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**[!UICONTROL Requisition List]**&#x200B;在`items_count`回應中傳回不正確的[!DNL GraphQL]。


<u>要再現的步驟</u>：

1. 啟用B2B **[!UICONTROL Requisition List]**&#x200B;功能。
1. 建立一些產品。
1. 建立客戶帳戶。
1. 按一下&#x200B;**[!UICONTROL Create new Requisition List]**。
1. 傳送包含產品的`addProductsToRequisitionList` [!DNL GraphQL]突變要求，以將其新增至[!UICONTROL Requisition List]。

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. 傳送`addProductsToRequisitionList` [!DNL GraphQL]突變要求，連同其他三個產品以新增至[!UICONTROL Requisition List]。
1. 檢查回應中的`items_count`。

**預期結果**：

* `items_count`：回應中應傳回4個。

**實際結果**：

* `items_count`：回應中傳回2。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
