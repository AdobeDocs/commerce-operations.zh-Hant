---
title: ACSD-54319：產品價格在*[!UICONTROL Products in Carts]*報表中顯示為零
description: 套用ACSD-54319修補程式，修正*[!UICONTROL Products in Carts]*報表中產品價格為零的Adobe Commerce問題
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319：產品價格在&#x200B;*[!UICONTROL Products in Carts]*&#x200B;報表中顯示為零

ACSD-54319修補程式修正了&#x200B;*[!UICONTROL Products in Carts]*&#x200B;報告中產品價格為零的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54319。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品價格在&#x200B;*[!UICONTROL Products in Carts]*&#x200B;報表中顯示為零。

<u>要再現的步驟</u>：

1. 從&#x200B;**[!UICONTROL Catalog Price Scope]** > **[!UICONTROL Website]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]**&#x200B;將&#x200B;**[!UICONTROL Price]**&#x200B;設定為&#x200B;**[!UICONTROL Catalog Price Scope]**。
1. 從&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;建立第二個網站。
1. 從&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;建立產品。
1. 僅將此產品指派給第二個網站。
1. 從第二個網站新增產品至購物車。
1. 移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]**&#x200B;格線。
1. 檢查&#x200B;*[!UICONTROL Price]*&#x200B;格線中的&#x200B;*[!UICONTROL Products In Carts]*&#x200B;欄。

<u>預期結果</u>：

*[!UICONTROL Products in Carts]*&#x200B;報表格中的產品價格不是零。

<u>實際結果</u>：

*[!UICONTROL Products in Carts]*&#x200B;報表格中的產品價格為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
