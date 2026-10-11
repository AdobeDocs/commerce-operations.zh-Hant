---
title: ACSD-45168：並未針對已覆寫url_key屬性的產品產生SEO友善URL
description: 套用ACSD-45168修補程式以修正Adobe Commerce問題，該問題導致未針對在商店檢視層級上覆寫url_key屬性的產品產生SEO易記URL。
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%
---
# ACSD-45168：並未針對已覆寫url_key屬性的產品產生SEO友善URL

ACSD-45168修補程式針對在商店檢視層級上覆寫url_key屬性的產品，未產生SEO易記URL的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-45168。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對於在存放區檢視層級上覆寫url_key屬性的產品，不會產生SEO友善URL。

<u>要再現的步驟</u>：

1. 依下列方式設定設定，方法是前往「**[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**」：
   * [!UICONTROL Use Categories Path for Product URLs] = *是*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *是*
1. 清除設定快取。
1. 建立兩個類別： [!UICONTROL Category 1]和[!UICONTROL Category 2]。
1. 建立兩個產品： [!UICONTROL Category 1]中的[!UICONTROL Product 1]，[!UICONTROL Category 1]中的[!UICONTROL Product 2]。
1. 將[!UICONTROL Product 1]的範圍變更為[!UICONTROL Default Store View]。
1. 取消核取[!UICONTROL Search Engine Optimization]中的選用URL [!UICONTROL Key]。
1. 儲存產品。
1. 切換回[!UICONTROL All Store Views]。
1. 將[!UICONTROL Product 1]新增至[!UICONTROL Category 2]，並將[!UICONTROL Product 2]新增至[!UICONTROL Category 2]。
1. 檢查`url_rewrite`資料表或[!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites]。

<u>預期結果</u>：

已為[!UICONTROL Product 1]建立[!UICONTROL Category 2]的SEO友善URL。

<u>實際結果</u>：

[!UICONTROL Product 1]遺失[!UICONTROL Category 2]的SEO易記URL，因為它已覆寫存放區檢視範圍的URL索引鍵屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
