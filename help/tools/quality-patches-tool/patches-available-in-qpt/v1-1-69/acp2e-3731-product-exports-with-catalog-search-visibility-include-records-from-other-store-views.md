---
title: ACP2E-3731：具有[!UICONTROL Catalog, Search]可見度的產品匯出包含其他商店檢視的記錄
description: 套用ACP2E-3731修補程式以修正Adobe Commerce，其中可見性篩選器設為[!UICONTROL Catalog, Search]的產品匯出專案會因市集範圍的屬性變化而在多存放區設定中包含不正確的列。
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731：具有[!UICONTROL Catalog, Search]可見度的產品匯出包含其他商店檢視的記錄

ACP2E-3731修補程式修正了在多商店環境中，具有&#x200B;*[!UICONTROL Catalog, Search]*&#x200B;可見度的產品匯出錯誤包含其他商店檢視的記錄的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACP2E-3731。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p9

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當可見性篩選器在多存放區設定中設定為&#x200B;*[!UICONTROL Catalog, Search]*&#x200B;時，由於存放區範圍的屬性變化，產品匯出包含不正確的列。

<u>要再現的步驟</u>：

1. 在[管理]面板中，移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;以建立其他網站、商店和商店檢視。
1. 移至&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**。 按一下&#x200B;**[!UICONTROL Add Attribute Set]**&#x200B;以建立屬性。 將&#x200B;**[!UICONTROL Based On]**&#x200B;設定為&#x200B;*預設*。
1. 建立產品並將其指派給主要網站和次要網站。
1. 為新建立的屬性設定文字值，並將&#x200B;**[!UICONTROL Scope]**&#x200B;設定為&#x200B;*所有存放區檢視*。
1. 將範圍變更為次要存放區檢視，並使用不同的值更新屬性。
1. 將範圍變更為預設商店檢視和次要商店檢視，然後將產品可見性設定為&#x200B;*個別不可見*。
1. 移至&#x200B;**[!UICONTROL System]** > **[!UICONTROL Export]**，然後從下拉式功能表中選取&#x200B;*產品*。
1. 設定&#x200B;**[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]*&#x200B;的篩選器，然後按一下&#x200B;**[!UICONTROL Continue]**。
1. 執行以下命令以處理匯出：

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. 檢查匯出的檔案。

<u>預期結果</u>：

僅匯出篩選的記錄。

<u>實際結果</u>：

匯出的檔案包含次要存放區檢視的列，這不符合匯出期間設定的篩選條件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
