---
title: ACSD-61322：未指派給[!UICONTROL Shared Catalogue]的產品包含在XML網站地圖
description: 套用ACSD-61322修補程式以修正Adobe Commerce未指派給預設（一般）群組[!UICONTROL Shared Catalog]的產品/類別仍包含在XML網站地圖中的問題。
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322：未指派給[!UICONTROL Shared Catalogue]的產品包含在XML網站地圖

ACSD-61322修補程式修正未指派給預設（一般）群組[!UICONTROL Shared Catalog]的產品/類別仍包含在XML網站地圖中的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-61322。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未指派給預設（一般）群組[!UICONTROL Shared Catalog]的產品/類別仍包含在XML網站地圖。

<u>要再現的步驟</u>：

1. 建立一些類別並新增產品（例如，類別1和類別2）。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**」並啟用&#x200B;*[!UICONTROL Company and Shared Catalog]*。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;並修改預設目錄。
1. 從&#x200B;**[!UICONTROL Select]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Set Pricing and Structure]**，然後按一下&#x200B;**[!UICONTROL Configure]**。
1. 在「*類別1 >類別2*」類別下，取消選取部分不應在[!UICONTROL Shared Catalog]中的產品。
1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;並產生目錄。
1. 在店面，建立客戶帳戶。
1. 移至&#x200B;*類別1 >類別2*&#x200B;類別。 它只會顯示指派給[!UICONTROL Shared Catalog]的產品。
1. 前往「**[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]**」並產生新的Sitemap。
1. 開啟店面上的`sitemap.xml`。
1. 搜尋您未包含在[!UICONTROL Shared Catalog]中的產品。

<u>預期結果</u>：

Sitemap不包含未指派給[!UICONTROL Shared Catalog]之產品和類別的連結。

<u>實際結果</u>：

Sitemap包含未指派給[!UICONTROL Shared Catalog]之產品和類別的連結。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
