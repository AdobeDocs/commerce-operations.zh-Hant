---
title: ACSD-48234：啟用[!UICONTROL Display Out of Stock Products]時，目錄搜尋結果類別專案計數不正確
description: 套用ACSD-48234修補程式以修正Adobe Commerce問題，此問題發生在啟用[!UICONTROL Display Out of Stock Products]選項時，目錄搜尋結果顯示錯誤的類別專案計數。
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%
---
# ACSD-48234：目錄搜尋結果顯示不正確的類別專案計數&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;已啟用

ACSD-48234修補程式解決啟用&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;選項時，目錄搜尋結果顯示不正確的類別專案計數的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-48234。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。


## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;選項時，目錄搜尋結果會顯示不正確的類別專案計數。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**」並開啟「**[!UICONTROL color]**」屬性。
1. 新增兩個選項，例如橘色和綠色。 儲存屬性。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**」並將&#x200B;**[!UICONTROL color]**&#x200B;屬性新增至「**[!UICONTROL Default]**」屬性集。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**，並將&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;設為&#x200B;_是_。
1. 建立類別「cat1」。
1. 建立兩個產品：
   1. 名稱：prod1，顏色：橘色，類別：cat1。
   1. 名稱：prod2，顏色：綠色，類別：cat1。
1. 開啟店面上的cat1類別。
1. 在圖層導覽中選取橘色。

<u>預期結果</u>：

只顯示prod1產品。

<u>實際結果</u>：

prod1和prod2產品都會顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
