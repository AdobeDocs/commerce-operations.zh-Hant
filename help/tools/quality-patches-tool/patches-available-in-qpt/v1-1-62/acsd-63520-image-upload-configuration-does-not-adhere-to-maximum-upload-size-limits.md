---
title: ACSD-63520：透過影像上傳設定上傳的影像超過設定的大小限制
description: 套用ACSD-63520修補程式，修正Adobe Commerce問題，該問題導致透過管理面板中的影像上傳設定上傳的影像未遵守已設定的最大上傳大小限制。
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63520：透過[!UICONTROL Image Upload Configuration]上傳的影像超過設定的大小限制

ACSD-63520修補程式解決透過[!UICONTROL Images Upload Configuration]上傳的影像不符合設定的最大上傳大小限制的問題。 若要解決此問題，請在[!UICONTROL Admin]面板中設定[!UICONTROL Images Upload Configuration]設定。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 修補程式ID為ACSD-63520。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的[!DNL Adobe Commerce]版本相容，請將`magento/quality-patches`套件更新為最新版本，並在[[!DNL Quality Patches Tool]：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)上檢查相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過[!UICONTROL Admin]面板中的[!UICONTROL Images Upload Configuration]上傳的影像未遵守上傳大小上限。

<u>要再現的步驟</u>：

1. 登入&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
1. 導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]**」並設定：
   * 品質：100
   * 啟用前端調整大小：是
   * 最大寬度：800
   * 最大高度：600
1. 展開&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;並設定：
   * 啟用影像最佳化：是
   * 最大寬度：1000
   * 最大高度：1000
1. 導覽至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**。
   1. 新增&#x200B;**[!UICONTROL Product Name]**、**[!UICONTROL SKU]**&#x200B;和&#x200B;**[!UICONTROL Price]**。
   1. 按一下&#x200B;**[!UICONTROL Create Configurations]**、選取&#x200B;**[!UICONTROL Attributes]**，然後按一下&#x200B;**[!UICONTROL Next]**。
   1. 選擇大小(S、M、L、XL)，按一下&#x200B;**[!UICONTROL Next]**。
   1. 在&#x200B;**[!UICONTROL Images]**&#x200B;下，選取&#x200B;**[!UICONTROL Apply single set of images to all SKUs]**。
   1. 上傳影像（至少1024x1024），按一下&#x200B;**[!UICONTROL Next]**。
   1. 按一下&#x200B;**[!UICONTROL Generate Product]**。
1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

影像應遵循設定的上傳大小和調整大小限制。

<u>實際結果</u>：

影像沒有調整大小，且超過設定的上傳大小限制。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
