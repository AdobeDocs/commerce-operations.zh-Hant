---
title: 「ACSD-47803：沒有庫存的可設定產品色票顯示為可用」
description: 套用ACSD-47803修補程式，以修正Adobe Commerce無庫存可設定產品色票顯示為可用的問題。
feature: Configuration, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803：未備貨的可設定產品色票顯示為可用

ACSD-47803修補程式修正無庫存可設定產品色票顯示為可用的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-47803。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

沒有庫存的可設定產品色票會依可用狀態顯示。

<u>要再現的步驟</u>：

>[!NOTE]
>
>以下步驟參考範例資料作為範例。

1. 在[!UICONTROL Commerce] Admin中，移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**，並將&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;設為&#x200B;*是*。
1. 再次從管理員導覽至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，並在產品編輯頁面中編輯可設定的產品（例如「WB04」 SKU，如果您使用範例資料）：
   * 若為其中一個組態變體，請將數量設定為&#x200B;*0* （例如「WB04-M-Purple」）。
1. 現在，在店面開啟可設定的產品。
1. 選取零庫存（即「M」）的可設定變體的產品大小。

<u>預期結果</u>：

無庫存的選項已停用並標示為[!UICONTROL Out of Stock]。

<u>實際結果</u>：

已啟用所有色票，即使是[!UICONTROL Out of Stock]色票亦然。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
