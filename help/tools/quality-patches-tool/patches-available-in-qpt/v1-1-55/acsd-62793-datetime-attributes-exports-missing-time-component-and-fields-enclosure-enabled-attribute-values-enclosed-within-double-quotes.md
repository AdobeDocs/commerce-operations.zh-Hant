---
title: ACSD-62793：匯出中的Datetime屬性遺失時間元件。 此外，如果已啟用**[!UICONTROL Fields Enclosure]**，屬性值會以雙引號括住
description: 套用ACSD-62793修補程式，修正匯出資料中的日期時間屬性遺失時間元件的Adobe Commerce問題。 此外，如果已啟用**[!UICONTROL Fields Enclosure]**，則*additional_attributes*欄中的屬性值將會括在雙引號中。
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
source-git-commit: 1645006f142c902ac729a99502f59b6d42266691
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# ACSD-62793：匯出中的Datetime屬性遺失時間元件。 此外，如果啟用&#x200B;**[!UICONTROL Fields Enclosure]**，屬性值會以雙引號括住

ACSD-62793修補程式修正匯出資料中的日期時間屬性遺失時間元件的問題。 此外，如果已啟用&#x200B;**[!UICONTROL Fields Enclosure]**，*additional_attributes*&#x200B;資料行中的屬性值將會括在雙引號中。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-62793。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯出資料中的日期時間屬性不包含時間元件。 此外，如果已啟用&#x200B;**[!UICONTROL Fields Enclosure]**，*additional_attributes*&#x200B;資料行中的屬性值將會括在雙引號中。

<u>要再現的步驟</u>：

1. 建立具有&#x200B;**[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**&#x200B;的產品屬性。
1. 將屬性指派給&#x200B;**[!UICONTROL Default]**&#x200B;屬性集。
1. 為新屬性建立具有日期和時間值的簡單產品。
1. 從&#x200B;**[!UICONTROL System]** > *資料傳輸* > **[!UICONTROL Export]**&#x200B;將產品匯出至CSV檔案。
1. 檢查&#x200B;*additional_attributes*&#x200B;欄中的屬性值。 它只有日期部分，但沒有時間。
1. 更新屬性值以使用時間，例如&quot;08/10/22， 3:20 PM&quot;。
1. 匯入CSV檔案。
1. 檢查&#x200B;*catalog_product_entity_datetime*&#x200B;表格。

<u>預期結果</u>：

日期與時間會正確匯出和匯入。

<u>實際結果</u>：

只匯出和匯入日期零件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
