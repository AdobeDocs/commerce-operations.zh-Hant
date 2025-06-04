---
title: ACSD-65100：移除[!UICONTROL Media Gallery Image Optimization]設定中的[!UICONTROL Maximum Width]和[!UICONTROL Maximum Height]值會導致錯誤
description: 套用ACSD-65100修補程式以修正Adobe Commerce問題，其中移除[!UICONTROL Media Gallery Image Optimization]設定中的[!UICONTROL Maximum Width]和[!UICONTROL Maximum Height]值會在影像最佳化程式期間導致錯誤。
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100：移除[!UICONTROL Media Gallery Image Optimization]設定中的[!UICONTROL Maximum Width]和[!UICONTROL Maximum Height]值會導致錯誤

ACSD-65100修補程式修正了移除&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;設定中的&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;值會在影像最佳化程式期間導致錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65100。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

影像最佳化程式期間，在&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;設定中移除&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;的值時發生錯誤。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**」。
1. 移除&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;的值。
1. 清除設定快取。
1. 導覽至&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**。
1. 開啟任何頁面進行編輯。
1. 在內容區域中：
   1. 選取&#x200B;**[!UICONTROL Add Layout]** > **[!UICONTROL Row]**。
   1. 選取&#x200B;**[!UICONTROL Add Elements]** > **[!UICONTROL Text]**。
   1. 在WYSIWYG編輯器中，按一下&#x200B;**[!UICONTROL Add Image]**。
   1. 上傳影像並選取&#x200B;**[!UICONTROL Add Selected]**。
1. 檢查`var/log/exception.log`檔案。

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

會記錄類似下列的錯誤：

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
