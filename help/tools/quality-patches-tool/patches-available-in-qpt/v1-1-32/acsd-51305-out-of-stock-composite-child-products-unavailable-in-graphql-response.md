---
title: 'ACSD-51305：GraphQL回應中無法使用無庫存複合子產品'
description: 套用ACSD-51305修補程式以修正Adobe Commerce回應中無法使用無庫存複合子產品的GraphQL問題。
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305：GraphQL回應中無法使用無庫存複合子產品

ACSD-51305修補程式修正GraphQL回應中無法使用無庫存複合子產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51305。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL回應中無法使用無庫存複合子產品。

<u>要再現的步驟</u>：

1. 登入Admin網站。
1. 建立類別(cat1，id=3)。
1. 建立&#x200B;*simple1*&#x200B;產品（無庫存、未個別顯示、已指派給&#x200B;*cat1*）。
1. 建立&#x200B;*simple2*&#x200B;產品（有庫存，未個別顯示，已指派給&#x200B;*cat1*）。
1. 建立包含&#x200B;*simple1*&#x200B;和&#x200B;*simple2*&#x200B;子產品的&#x200B;*套件1*&#x200B;產品作為選項按鈕&#x200B;*option1*&#x200B;產品，並將其指派給&#x200B;*cat1*&#x200B;類別。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**」。

   * 將&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;設為&#x200B;*是*。

1. 開啟店面上的&#x200B;*bundle1*&#x200B;產品，並確定其中同時顯示&#x200B;*simple1*&#x200B;和&#x200B;*simple2*&#x200B;子產品。
1. 執行下列GraphQL查詢：

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>預期結果</u>：

**[!UICONTROL Options]**&#x200B;區塊內的&#x200B;**[!UICONTROL Product]**&#x200B;區段不是空的。

<u>實際結果</u>：

**[!UICONTROL Options]**&#x200B;區塊內的&#x200B;**[!UICONTROL Product]**&#x200B;區段是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
