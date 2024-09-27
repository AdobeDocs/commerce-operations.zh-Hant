---
title: 「ACSD-60538：如果在[!UICONTROL All Store Views]中停用產品，則屬性無法正確顯示」
description: 套用ACSD-60538修補程式以修正Adobe Commerce問題，若產品在*所有商店檢視*中停用，並只在特定商店檢視範圍中啟用，則產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示。
feature: Attributes, GraphQL
role: Admin, Developer
source-git-commit: c394e003797d8095c17a0f6047024231e26a8321
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538：如果在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中停用產品，則屬性無法正確顯示

ACSD-60538修補程式修正了產品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中停用，且只在特定商店檢視範圍中啟用的情況下，產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-60538。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果產品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中停用，並且只在特定的存放區檢視範圍中啟用，則產品屬性在GraphQL回應中無法正確顯示，導致產品無法正確顯示。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 建立可設定的產品包含&#x200B;*color*&#x200B;屬性和三個子產品（*藍色*、*黑色*&#x200B;和&#x200B;*棕色*）。
1. 停用&#x200B;*[!UICONTROL All Store Views]*&#x200B;範圍上兩個關聯的子產品（*藍色*&#x200B;和&#x200B;*黑色*）。
1. 移至&#x200B;**[!UICONTROL Store View]**&#x200B;範圍。
1. 在&#x200B;*[!UICONTROL Store View]*&#x200B;範圍上啟用子產品（*藍色*&#x200B;和&#x200B;*黑色*）。
1. 執行以下GraphQL請求：

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>預期結果</u>：

GraphQL回應包含在&#x200B;*[!UICONTROL All Store Views]*&#x200B;上停用並在&#x200B;*[!UICONTROL Store View]*&#x200B;範圍上啟用的子關聯產品的屬性值。

<u>實際結果</u>：

產品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;上停用並在&#x200B;*[!UICONTROL Store View]*&#x200B;範圍上啟用時，GraphQL回應的子關聯產品屬性值為空白。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。