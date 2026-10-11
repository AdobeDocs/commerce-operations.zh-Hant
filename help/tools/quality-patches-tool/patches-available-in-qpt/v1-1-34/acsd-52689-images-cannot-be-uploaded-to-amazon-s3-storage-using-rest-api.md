---
title: ACSD-52689：影像無法透過REST API上傳至Amazon S3儲存空間
description: 套用ACSD-52689修補程式，修正Adobe Commerce無法透過REST API將影像上傳至Amazon S3儲存空間的問題。
feature: REST, Storage, Iaas
role: Admin
exl-id: 4d7a8ea7-2856-4b40-a922-fdd356dcaea4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: df5e974b-6742-4873-a687-a6bedaafdaa2
    internal-label: IaaS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# ACSD-52689：影像無法透過REST API上傳至Amazon S3儲存空間

ACSD-52689修補程式修正無法使用REST API將影像上傳到Amazon S3儲存空間的問題。安裝[!DNL Quality Patches Tool (QPT)] 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-52689。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法使用REST API將影像上傳至Amazon S3儲存空間

<u>要再現的步驟</u>：

1. 設定Amazon S3貯體的REMOTE_STORAGE 。
1. 使用大量API將影像新增到產品中。

   `POST .../rest/all/async/bulk/V1/products/bySku/media`

   ```text
   [
       {
           "sku": "p1",
           "entry": {
               "media_type": "image",
               "position": 0,
               "disabled": false,
               "types": [
                   "image",
                   "thumbnail",
                   "small_image",
                   "swatch_image"
               ],
               "content": {
                "type": "image\/jpeg",
                   "name": "adobe_commerce_test_3",
                   "base64_encoded_data": "/9j/4AAQSkZJRgABAQAAAQABA..."
               }
           }
       }
   ]
   ```

1. 等候處理大量作業。

<u>預期結果</u>

影像應上傳至Amazon S3貯體。

<u>實際結果</u>

影像不會自動上傳至Amazon S3貯體。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
