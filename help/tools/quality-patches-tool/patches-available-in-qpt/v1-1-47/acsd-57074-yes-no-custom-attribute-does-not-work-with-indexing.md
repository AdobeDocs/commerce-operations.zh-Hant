---
title: 「ACSD-57074：*是/否*在'attribute_code'屬性中具有'price_*'首碼的自訂屬性不適用於索引」
description: 套用ACSD-57074修補程式來修正Adobe Commerce問題，亦即「attribute_code」屬性中首碼為「price_*」的*Yes/No*自訂屬性無法與索引搭配運作。
feature: Products, Categories, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074： *是/否`attribute_code`屬性中具有`price_*`首碼的*&#x200B;自訂屬性不適用於索引

ACSD-57074修補程式修正了`attribute_code`屬性中首碼為`price_*`的&#x200B;*是/否*&#x200B;自訂屬性無法與索引搭配使用的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47時，即可使用此修補程式。 修補程式ID為ACSD-57074。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`attribute_code`屬性中具有`price_*`首碼的&#x200B;*是/否*&#x200B;自訂屬性無法與索引搭配使用。

<u>要再現的步驟</u>：

1. 使用下列選項建立自訂產品屬性：
   * *[!UICONTROL Catalog Input Type]*： *是/否*
   * *[!UICONTROL Scope]*： *StoreView*
   * *[!UICONTROL Use in Search]*： *是*
1. 將屬性指定給預設屬性集。
1. 使用我們建立的屬性建立產品。
1. 將我們剛建立的產品指派至類別。
1. 執行完整重新索引。

<u>預期結果</u>：

產品會顯示在指派的類別中。

<u>實際結果</u>：

產品未出現在類別首頁。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
