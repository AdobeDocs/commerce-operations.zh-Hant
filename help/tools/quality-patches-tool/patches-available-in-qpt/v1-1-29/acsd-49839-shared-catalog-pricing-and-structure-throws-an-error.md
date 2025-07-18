---
title: ACSD-49839：共用目錄定價和結構擲回錯誤
description: 套用ACSD-49839修補程式以修正Adobe Commerce問題，該問題導致當產品在SKU中有單引號或雙引號時，共用目錄定價和結構在管理員中擲回錯誤。
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839：共用目錄定價和結構擲回錯誤

ACSD-49839修補程式修正當產品在SKU中有單引號或雙引號時，共用目錄定價和結構在管理員中擲回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49839。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當產品在SKU中有單引號或雙引號時，共用目錄定價和結構會在管理員中擲回錯誤。

<u>要再現的步驟</u>：

1. 使用特殊字元（即雙引號）設定某些產品SKU，例如：
   *[Product&quot;12， Product&quot;14， Product&quot;15]*。
1. 移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** （例如&#x200B;*[測試共用目錄]*）。
1. 指派全部&#x200B;**[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**」。
1. 標籤&#x200B;*[!UICONTROL Root Catalog]*&#x200B;以選取所有類別和產品。
1. 在網路面板中觀察AJAX請求。

<u>預期結果</u>：

當產品在SKU中有單引號或雙引號時，共用的目錄定價和結構不會在管理員中擲回錯誤。

<u>實際結果</u>：

當產品在SKU中有單引號或雙引號時，共用的目錄定價和結構會在管理員中擲回錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
