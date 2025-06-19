---
title: ACSD-54776：未勾選[!UICONTROL Use Default Value]，第二個網站、商店和商店檢視不會儲存非預設產品欄位值
description: 套用ACSD-54776修補程式以修正未核取的[!UICONTROL Use Default Value]和非預設產品欄位值未儲存至第二個網站、商店和商店檢視的Adobe Commerce問題。
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776：未勾選&#x200B;*[!UICONTROL Use Default Value]*&#x200B;且未儲存非預設產品欄位值

>[!NOTE]
>
>此修補程式取代了QPT 1.1.35中發行的[ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md)修補程式。

ACSD-54776修補程式修正未核取的&#x200B;**[!UICONTROL Use Default Value]**&#x200B;和非預設產品欄位值未儲存至第二個網站、商店和商店檢視的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-54776。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p4、2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未勾選的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;以及未儲存第二個網站、商店和商店檢視的非預設產品欄位值。

<u>要再現的步驟</u>：

1. 前往後端，導覽至「**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**」並建立新的網站、商店和商店檢視。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，建立簡單產品並儲存，然後從&#x200B;**[!UICONTROL Product in Websites]**&#x200B;將產品指派給兩個網站。
1. 從步驟2將範圍變更為新建立的存放區檢視。
1. 移至&#x200B;**[!UICONTROL Search Engine Optimization]**&#x200B;並取消勾選[!UICONTROL Meta Title]、[!UICONTROL Meta Keywords]和[!UICONTROL Meta Description]的&#x200B;**[!UICONTROL Use Default Value]**&#x200B;核取方塊。
1. 清除欄位中的文字： *[!UICONTROL Meta Title]*、*[!UICONTROL Meta Keywords]*&#x200B;和&#x200B;*[!UICONTROL Meta Description]*，然後按一下&#x200B;**[!UICONTROL Save]**。
1. 再次移至&#x200B;**[!UICONTROL Search Engine Optimization]**。

<u>預期結果</u>

會儲存欄位值及核取方塊。

<u>實際結果</u>

未儲存欄位和核取方塊的值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant>)。
