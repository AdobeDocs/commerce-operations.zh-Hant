---
title: ACSD-47657：新增AWS憑證的快取機制
description: 套用ACSD-47657修補程式，透過新增Adobe Commerce憑證的快取機制，修正AWS S3高負載請求期間發生的AWS問題。
feature: Cache
role: Admin, Developer
exl-id: 2851d511-a9b0-49f8-94ba-ad63d2397ca5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-47657：新增AWS憑證的快取機制

ACSD-47657修補程式修正了高載入AWS S3請求期間發生的問題，方法是新增AWS憑證的快取機制。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-47657。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

為從AWS擷取的AWS憑證新增快取機制，以進行EC2設定。

<u>要再現的步驟</u>：

1. 為Adobe Commerce啟用AWS S3貯體儲存：

   ```
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="magentopubmedia-prod" --remote-storage-region="aws-west" --no-interaction
   bin/magento config:set 
   system/media_storage_configuration/media_database 0 
   bin/magento cache:flush
   ```

1. 執行同步處理：

   ```
   bin/magento remote-storage:sync
   ```

<u>預期結果</u>：

同步化成功完成。

<u>實際結果</u>：

大約一小時後，發生下列錯誤：

```
    report.CRITICAL: Aws\Exception\CredentialsException: Error retrieving credentials from the instance profile metadata service. (cURL error 28: Connection timed out after 1001 milliseconds) (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) 
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
