---
title: ACSD-48210：存放區檢視特定範圍屬性會覆寫全域值
description: 套用ACSD-48210修補程式以修正Adobe Commerce更新特定存放區檢視中的*[!UICONTROL Website Scope]*屬性會覆寫全域範圍內的屬性值的問題。
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-48210：存放區檢視特定範圍屬性會覆寫全域值

ACSD-48210修補程式修正了在特定存放區檢視中更新&#x200B;*[!UICONTROL Website Scope]*&#x200B;屬性時，會覆寫全域範圍中屬性值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-48210。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新特定存放區檢視中的&#x200B;*[!UICONTROL Website Scope]*&#x200B;屬性時，會覆寫全域範圍內的屬性值。

匯入產品價格時，多個資料列共用相同的`SKU`和`store_view_code`，導致&#x200B;*[!UICONTROL All Store View]*&#x200B;和&#x200B;*[!UICONTROL Default Store]*&#x200B;範圍內的價格更新不正確。 修改特定存放區檢視中的網站範圍屬性時，不再覆寫全域範圍中的屬性值。
<u>要再現的步驟</u>：

1. 將&#x200B;*[!UICONTROL Catalog Price Scope]*&#x200B;設定為&#x200B;*[!UICONTROL Website]*。
1. 建立名為&#x200B;*SP01*&#x200B;的簡單產品，並將價格設定為&#x200B;*$84.50*。
1. 使用下面提供的CSV匯入產品：

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. 檢查&#x200B;*[!UICONTROL All Store View]*&#x200B;和&#x200B;*[!UICONTROL Default Store]*&#x200B;範圍中的產品價格。

<u>預期結果</u>：

* 第一個非空白值用於&#x200B;*[!UICONTROL Default Store]*&#x200B;範圍。
* *[!UICONTROL All Store View]*&#x200B;範圍維持不變。

<u>實際結果</u>：

* *[!UICONTROL All Store View]*&#x200B;範圍價格變更為&#x200B;*$86.59*。
* *[!UICONTROL Default Store]*&#x200B;範圍價格變更為&#x200B;*$86.59*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
