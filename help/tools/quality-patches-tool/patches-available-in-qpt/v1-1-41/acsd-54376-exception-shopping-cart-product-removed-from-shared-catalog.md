---
title: 'ACSD-54376：從[!UICONTROL shared catalog]移除產品時，購物車發生例外狀況'
description: 套用ACSD-54376修補程式以修正Adobe Commerce問題，該問題導致當產品在加入購物車後從[!UICONTROL shared catalog]中移除時，在購物車中發生例外狀況。
feature: Shopping Cart, B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376：從[!UICONTROL shared catalog]移除產品時，購物車發生例外狀況

ACSD-54376修補程式修正了當產品在加入購物車後從[!UICONTROL shared catalog]中移除時，購物車中發生例外狀況的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41時，即可使用此修補程式。 修補程式ID為ACSD-54376。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當產品在加入購物車後從[!UICONTROL shared catalog]中移除時，購物車中會發生例外狀況。

<u>要再現的步驟</u>：

1. 使用B2B安裝Adobe Commerce。
1. 啟用[!UICONTROL shared catalog]。
1. 建立產品並將其指派給預設[!UICONTROL shared catalog]。
1. 從店面新增產品至購物車。
1. 從[!UICONTROL shared catalog]移除產品。
1. 使用迷你購物車下拉式清單，導覽至結帳頁面。

<u>預期結果</u>：

例外狀況會得到處理，不會顯示給您。

<u>實際結果</u>：

未處理的例外狀況會顯示在結帳頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
