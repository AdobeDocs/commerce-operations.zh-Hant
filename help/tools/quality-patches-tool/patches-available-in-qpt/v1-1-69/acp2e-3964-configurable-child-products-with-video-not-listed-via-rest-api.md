---
title: ACP2E-3964：可設定的子產品未透過REST API列出視訊
description: 套用ACP2E-3964修補程式以修正Adobe Commerce問題，此問題導致位於[!UICONTROL Media Gallery]中視訊的可設定產品子項產品無法透過REST API列出。
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964：可設定的子產品未透過REST API列出視訊

ACP2E-3964修補程式修正了&#x200B;**[!UICONTROL Media Gallery]**&#x200B;中視訊可設定之產品的子產品無法透過REST API列出的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACP2E-3964。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法透過REST API列出視訊在&#x200B;**[!UICONTROL Media Gallery]**&#x200B;中的可設定產品的子產品，導致錯誤回應。

<u>要再現的步驟</u>：

1. 建立新的可設定產品並新增單一子產品。
1. 編輯子產品並在&#x200B;**[!UICONTROL Images and Videos]**&#x200B;下新增視訊(例如，[https://vimeo.com/1084537](https://vimeo.com/1084537))。
1. 儲存子產品。
1. 使用Admin Bearer權杖將GET要求傳送至REST API端點： `rest/v1/configurable-products/%sku%/children`。

<u>預期結果</u>：

REST API應該會傳回未發生錯誤的子產品資料，包括&#x200B;**[!UICONTROL Media Gallery]**&#x200B;中的視訊資訊。

<u>實際結果</u>：

REST API傳回錯誤：

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
