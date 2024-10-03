---
title: 「ACSD-59925：在GraphQL中依位置排序[!UICONTROL Media Gallery]中的專案」
description: 套用ACSD-59925修補程式以修正Adobe Commerce問題，該問題導致[!UICONTROL Media Gallery]中的專案未依位置排序，進而導致顯示順序不正確。
feature: Media, GraphQL
role: Admin, Developer
source-git-commit: 97e3ab77e7c8f5f1efd9b616b5e1d198a1b41ab0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925：在GraphQL中依位置排序[!UICONTROL Media Gallery]中的專案

ACSD-59925修補程式修正[!UICONTROL Media Gallery]中的專案未依位置排序，導致顯示順序不正確的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-59925。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Media Gallery]中的專案未依位置排序，導致顯示順序不正確。

<u>要再現的步驟</u>：

1. 建立/編輯產品。
1. 新增兩個或多個影像並儲存。
1. 編輯相同的產品，但這次請將最後一個影像拖曳到第一個位置。
1. 儲存產品。
1. 重新索引。
1. 前往GraphQL使用者端。
1. 執行GraphQL查詢：

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u>預期結果</u>：

`media_gallery`中的專案是依位置排序。

<u>實際結果</u>：

`media_gallery`中的專案未依位置排序。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。