---
title: BB2B-2598：新增快取功能以儲存storeConfig、貨幣、國家/地區、availableStores GraphQl查詢
description: 套用BB2B-2598修補程式，將快取功能新增至storeConfig、貨幣、國家/地區、以及availableStores GraphQl查詢。
feature: B2B, GraphQL, Cache
role: Admin
exl-id: b842fab4-d2c0-4ef1-be13-182f09015cd7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# BB2B-2598：新增快取功能至`storeConfig`、`currency`、`country`、`countries`和`availableStores` GraphQl查詢

BB2B-2598修補程式新增快取功能至`storeConfig`、`currency`、`country`、`countries`和`availableStores` GraphQl查詢。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為BB2B-2598。 請注意，此問題已排程在Adobe Commerce 2.4.7-beta1中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法快取`availableStores`、`countries`、`country`、`currency`、`storeConfig`和`customAttributeMetadata`個GraphQL查詢。

<u>必要條件</u>：

* 伺服器正在指向[!DNL Varnish]代理至Adobe Commerce後端。
* 組態設定`system/full_page_cache/caching_application`設為&#x200B;*2* ([!DNL Varnish])，或前往Adobe Commerce管理員> **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >並將其設為[!DNL Varnish]。

套用修補程式後，請執行以下步驟以確保快取功能現在可用：

1. 使用任意欄位，將`GET`要求傳送給以上列出的任何GraphQL查詢。
1. 重新傳送請求而不做任何變更；您會發現速度更快。 請注意，要求並未傳送至後端，但已由[!DNL Varnish]以快取點選的形式完全處理。
1. 如果需要進一步的校訂，請註解[VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227)中存在的`X-Magento-Debug`標頭未設定，然後重新啟動[!DNL Varnish]並再次執行上述步驟。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
