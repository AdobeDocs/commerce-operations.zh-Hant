---
title: ACSD-63299：店面未顯示可設定產品的特殊價格
description: 套用ACSD-63299修補程式，修正Adobe Commerce特殊價格屬性不再影響可設定產品之特殊價格顯示的問題。
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299：店面未顯示可設定產品的特殊價格

ACSD-63299修補程式修正了特殊價格屬性不再影響可設定產品之特殊價格的顯示問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63299。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在[!DNL Adobe Commerce]中，變更特殊價格屬性的&#x200B;*在產品清單中使用*&#x200B;值不再影響可設定產品的特殊價格的顯示方式。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**。
1. 尋找&#x200B;***[!UICONTROL special_price]***&#x200B;屬性並導覽至&#x200B;**[!UICONTROL Storefront Properties]**。
1. 將&#x200B;***[!UICONTROL Used in Product Listing]***&#x200B;變更為&#x200B;***[!UICONTROL No]***。
1. 建立一個可設定的產品以及一個子項：
   * 名稱和SKU：測試
   * 價格：$159.00
   * 根據顏色產生選項。 新增顏色：藍色
   * 儲存
1. 開啟子產品，然後依照下列步驟進行：
   * 在&#x200B;**[!UICONTROL Advanced Pricing]**&#x200B;中設定特殊價格為$99.90
   * 將[!UICONTROL Visibility]變更為&#x200B;**[!UICONTROL Catalog, Search]**。
1. 開啟簡單產品頁面，並確認可看見特殊價格。
1. 開啟可設定的產品頁面。
1. 選取藍色產品。

<u>預期結果</u>：

特殊價格的顯示方式與簡單產品相同。

<u>實際結果</u>：

1. 選取可設定產品時，會顯示完整價格。
1. *低至……*&#x200B;的部分($99.90)與實際價格($99.90 + $59.10 = $159.00)之間不相符。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
