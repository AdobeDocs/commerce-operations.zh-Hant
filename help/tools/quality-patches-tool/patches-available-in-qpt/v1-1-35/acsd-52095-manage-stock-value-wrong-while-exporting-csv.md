---
title: ACSD-52095：匯出CSV時管理股票值錯誤
description: 套用ACSD-52095修補程式，修正匯出CSV時，產品管理庫存值錯誤的Adobe Commerce問題。
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095：匯出CSV時[!UICONTROL Manage Stock]值錯誤

ACSD-52095修補程式修正匯出CSV時產品`manage_stock`值錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-52095。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯出後，CSV檔案中的`manage_stock`值未正確地設為0。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**&#x200B;並設定&#x200B;**[!UICONTROL Manage Stock]** = *[!UICONTROL No]*。
1. 建立新產品並儲存。
1. 前往&#x200B;**[!UICONTROL System]** > **[!UICONTROL Export]**。
1. 選取&#x200B;*[!UICONTROL Entity Type]* = *[!UICONTROL Products]*&#x200B;並匯出產品。
1. 檢查產生的CSV檔案： `manage_stock` = 0， `use_config_manage_stock` = 1。
1. 再次移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**，並設定&#x200B;**[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*。
1. 移至&#x200B;**系統** > **匯出**。
選取&#x200B;*[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*。
1. 檢查產生的CSV檔案： `manage_stock` = 0， `use_config_manage_stock` = 1。
1. 在Admin中開啟產品，前往&#x200B;**[!UICONTROL Advanced Inventory]**&#x200B;並檢查&#x200B;**[!UICONTROL Manage Stock]**&#x200B;值。

<u>預期結果</u>

為產品啟用&#x200B;**[!UICONTROL Manage Stock]**&#x200B;時，其值為&#x200B;*1*。

<u>實際結果</u>

為產品啟用&#x200B;**[!UICONTROL Manage Stock]**&#x200B;時，其值為&#x200B;*0*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant>)。
