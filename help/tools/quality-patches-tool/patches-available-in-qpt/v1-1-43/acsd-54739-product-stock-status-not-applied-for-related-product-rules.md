---
title: ACSD-54739： *[!UICONTROL Product Stock]*狀態未套用於*[!UICONTROL Related Product Rules]*
description: 套用ACSD-54739修補程式以修正*[!UICONTROL Product Stock]*未套用*[!UICONTROL Related Product Rules]*狀態的Adobe Commerce問題。
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739： *[!UICONTROL Product stock]*&#x200B;未套用&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;狀態

ACSD-54739修補程式修正&#x200B;*[!UICONTROL Product stock]*&#x200B;未套用&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;狀態的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-54739。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*[!UICONTROL Product stock]*&#x200B;未套用&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;狀態。

<u>要再現的步驟</u>：

1. 將&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;設定設為&#x200B;*是*。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]**」，並為促銷規則條件設定&#x200B;*是*。
1. 建立相關的產品規則。 移至「**[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]**」>新增具有屬性數量的條件（選取有庫存/無庫存）。
1. 檢查前端的產品。

<u>預期結果</u>：

由&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;所比對的有庫存/無庫存產品。

<u>實際結果</u>：

*[!UICONTROL Related Product Rules]*&#x200B;沒有庫存/沒有庫存的產品相符。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
