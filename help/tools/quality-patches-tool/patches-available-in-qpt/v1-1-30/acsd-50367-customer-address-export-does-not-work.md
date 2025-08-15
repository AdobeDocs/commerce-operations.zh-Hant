---
title: ACSD-50367：客戶地址匯出不適用於多選屬性
description: 套用ACSD-50367修補程式，修正建立不含值的多選**戶的「客戶地址」屬性時，客戶地址匯出無**運作的Adobe Commerce問題。
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367：客戶地址匯出無法運作

ACSD-50367修補程式修正建立不含值的多選&#x200B;**`Customer Address`**&#x200B;屬性時，無法匯出客戶地址的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-50367。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立不含值的多選&#x200B;**`Customer Address`**&#x200B;屬性時，無法匯出客戶地址。

<u>必要條件</u>：

建立具有地址的客戶。

<u>要再現的步驟</u>：

1. 在&#x200B;**`Customer Address`** > **[!UICONTROL Admin]** > **[!UICONTROL Stores]**&#x200B;中建立多重選取&#x200B;**[!UICONTROL Customer Addresses]**&#x200B;屬性。
1. 移至「**[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**」，然後選取「**`Customer Address`**」實體型別。
1. 匯出客戶地址。 您會看到未匯出任何內容。
1. 刪除多選&#x200B;**`Customer Address`**&#x200B;屬性，然後再次匯出客戶地址。 這次會產生地址的CSV檔案。

<u>預期結果</u>：

建立多選&#x200B;**`Customer Address`**&#x200B;屬性時，客戶地址可以匯出為CSV檔案。

<u>實際結果</u>：

建立多選&#x200B;**`Customer Address`**&#x200B;屬性時，無法將客戶地址匯出為CSV檔案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
