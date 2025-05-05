---
title: ACSD-47444：存取PHP 7.4上已知產品的特定非現有類別路徑時發生_[!UICONTROL Trying to access array offset on value of type bool]_錯誤
description: 套用ACSD-47444修補程式來修正PHP 7.4上存取已知產品的特定非現有類別路徑時發生_[!UICONTROL Trying to access array offset on value of type bool]_錯誤的Adobe Commerce問題。
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444：存取PHP 7.4上已知產品的特定非現有類別路徑時發生&#x200B;_[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;錯誤

ACSD-47444修補程式可解決在存取PHP 7.4上已知產品的特定非現有類別路徑時，您會看到&#x200B;_[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;錯誤的問題。安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在PHP 7.4上存取已知產品的特定非現有類別路徑時，您會遇到下列錯誤： _[!UICONTROL Trying to access array offset on value of type bool]_。

<u>必要條件</u>：

PHP 7.4。

<u>要再現的步驟</u>：

1. 建立新產品 — 名稱為「test」。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** >設定&#x200B;**[!UICONTROL Generate "category/product" URL Rewrites]** = _否_。
1. 前往店面並造訪URL，例如../abc/test.html （「abc」 — 不應存在）。

<u>預期結果</u>：

404頁。

<u>實際結果</u>：

500錯誤：

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
