---
title: ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*設定為Yes而沒有*[!UICONTROL Use in Search]*選項
description: 套用ACSD-50887修補程式以修正Adobe Commerce的問題，其中產品屬性屬性*[!UICONTROL Use in Search Results Layered Navigation]*可設為*Yes*，而*[!UICONTROL Use in Search]*選項也可設為*Yes*。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;設定為&#x200B;*是*，但不含&#x200B;*[!UICONTROL Use in Search]*&#x200B;選項

ACSD-50887修補程式修正了產品屬性屬性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可設為&#x200B;*是*，而&#x200B;*[!UICONTROL Use in Search]*&#x200B;選項卻未設為&#x200B;*是*&#x200B;的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-50887。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品屬性屬性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可設為&#x200B;*是*，而不需將&#x200B;*[!UICONTROL Use in Search]*&#x200B;選項也設為&#x200B;*是*。

這些設定是專為一起使用而設計。 套用修補程式後，當&#x200B;*[!UICONTROL Use in Search]*&#x200B;選項設為&#x200B;*No*&#x200B;時，會隱藏&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;選項以如同也設為&#x200B;*No*&#x200B;一樣運作。

<u>要再現的步驟</u>：

1. 在Admin中，瀏覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**，並建立具有多重選取型別的屬性並設定下列專案：

   * *[!UICONTROL Use in Search]=否*
   * *[!UICONTROL Use in Layered Navigation]= （任何選項）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=是*
   * *名稱= Test_attribute*
   * *選項*：
     * *貼紙*
     * *挑選器*

1. 將新屬性加入預設屬性集。
1. 建立兩個產品：

   1. 第一個產品：
      * 名稱=貼紙
      * 將價格、數量、重量設為1
      * Test_attribute =選取選項&#x200B;*貼紙*

   1. 第二個產品：
      * 名稱=選取器
      * 將價格、數量、重量設為1
      * Test_attribute =選取兩個選項

1. 執行`catalogsearch_fulltext`重新索引：

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 在店面搜尋單詞&#x200B;*貼紙*。

<u>預期結果</u>：

只傳回產品&#x200B;*貼紙*，因為當&#x200B;*[!UICONTROL Use in Search]*&#x200B;設定為&#x200B;*否*&#x200B;時，[!DNL Elasticsearch]將不會索引Test_attribute。

<u>實際結果</u>：

兩個產品都會傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
