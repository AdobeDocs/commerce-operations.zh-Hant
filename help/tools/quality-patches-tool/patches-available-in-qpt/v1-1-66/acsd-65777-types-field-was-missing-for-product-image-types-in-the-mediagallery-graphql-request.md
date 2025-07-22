---
title: ACSD-65777：「MediaGallery」GraphQL請求中的產品影像型別缺少「types」欄位
description: 套用ACSD-65777修補程式以修正「MediaGallery」GraphQL請求中產品影像型別缺少「types」欄位的Adobe Commerce問題。
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777： **[!UICONTROL types]** GraphQL請求中的產品影像型別缺少`MediaGallery`欄位

ACSD-65777修補程式修正&#x200B;**[!UICONTROL types]** GraphQL請求中產品影像型別缺少`MediaGallery`欄位的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-65777。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過&#x200B;**[!UICONTROL types]** GraphQL要求擷取媒體資料時，產品影像型別缺少`MediaGallery`欄位。

<u>要再現的步驟</u>：

1. 建立產品。
1. 將影像上傳至產品。
1. 使用下列GraphQL擷取媒體資料。

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>預期結果</u>：

`media_gallery` GraphQL介面應包含&#x200B;**[!UICONTROL types]**&#x200B;欄位。

<u>實際結果</u>：

`media_gallery`不包含媒體&#x200B;**[!UICONTROL types]**&#x200B;欄位。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
