---
title: ACSD-62428：目錄搜尋索引中的庫存狀態錯誤
description: 套用ACSD-62428修補程式，修正當SKU不是可搜尋的屬性時，目錄搜尋索引中的「is_out_of_stock」值設定不正確的問題。
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428：目錄搜尋索引中的庫存狀態錯誤

ACSD-62428修補程式修正了SKU屬性未設定為可搜尋時，目錄搜尋索引中的`is_out_of_stock`值設定為不正確值的問題。 此修補程式可用於[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56。修補程式ID為ACSD-62428。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當SKU未設定為可搜尋的屬性時，目錄搜尋索引中的`is_out_of_stock`值設定為不正確的值，導致不正確的庫存表示。

<u>要再現的步驟</u>：

1. 建立自訂[!UICONTROL Source]和自訂[!UICONTROL Stock]。
1. 建立三個簡單的產品，並將其詳細目錄指派給自訂[!UICONTROL Source]。 將這些產品指派至類別。
1. 將&#x200B;*[!UICONTROL Inventory (MSI) Indexer]*&#x200B;設定為&#x200B;*[!UICONTROL Update on Save]*&#x200B;以便輕鬆復寫。
1. 將&#x200B;*[!UICONTROL Source Item Status]*&#x200B;設定為&#x200B;*[!UICONTROL In Stock]*&#x200B;並指派&#x200B;*[!UICONTROL Quantity]*。
1. 儲存產品。
1. 導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**，然後開啟&#x200B;**[!UICONTROL SKU]**&#x200B;屬性。
1. 將&#x200B;*[!UICONTROL Use In]*&#x200B;設為&#x200B;*[!UICONTROL No]*。
1. 變更產品數量（確認未設為0）。
1. 儲存產品。

<u>預期結果</u>：

`is_out_of_stock`值準確地反映產品的庫存狀態，即使SKU不是可搜尋的屬性亦然。

<u>實際結果</u>：

`is_out_of_stock`值未正確設定為1，而且索引資料中沒有SKU屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
