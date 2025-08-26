---
title: ACSD-58131：由於0位元組影像檔案，舊媒體集無法載入影像
description: 套用ACSD-58131修補程式來修正目錄中有0位元組影像時，舊媒體庫無法轉譯影像的Adobe Commerce問題。
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131：由於0位元組影像檔案，舊媒體集無法載入影像

ACSD-58131修補程式修正目錄中有0位元組影像時，舊媒體庫無法轉譯影像的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-58131。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將0位元組影像放入媒體集目錄時，舊媒體集無法轉譯任何影像。 更新後的系統現在會略過無效的0位元組檔案，如預期顯示有效的影像，並針對每個無效檔案記錄警告。

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**」。
1. 將&#x200B;**[!UICONTROL Enable Old Media Gallery]**&#x200B;設為&#x200B;*是*。
1. 在`pub/media/wysiwyg`目錄中放置一些影像。
1. 使用`touch pub/media/wysiwyg/empty_image.png`在相同目錄中建立0位元組影像。
1. 透過任何內容下的頁面產生器(例如CMS區塊)，從`wysiwyg`目錄新增影像：
   1. 建立新區塊。 前往&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]**，然後按一下&#x200B;**[!UICONTROL Add New Block]**。
   1. 使用頁面產生器編輯內容區段。
   1. 在&#x200B;**[!UICONTROL Layout]**&#x200B;底下，將新的&#x200B;**[!UICONTROL Row]**&#x200B;拖曳到舞台。
   1. 展開&#x200B;**[!UICONTROL Media]**&#x200B;並將&#x200B;**[!UICONTROL Image]**&#x200B;預留位置拖曳到列中。
   1. 按一下&#x200B;**[!UICONTROL Select from Gallery]**。
   1. 選取`wysiwyg`目錄（如果預設未選取）。

<u>預期結果</u>：

即使0位元組影像（或任何其他檔案）存在，媒體集仍可正常運作。

<u>實際結果</u>：

媒體集無法從`wysiwyg`目錄載入任何影像，因為在`var/log/system.log`中記錄了一個嚴重錯誤：

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
