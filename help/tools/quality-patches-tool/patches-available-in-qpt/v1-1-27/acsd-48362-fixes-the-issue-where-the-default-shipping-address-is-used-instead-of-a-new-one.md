---
title: ACSD-48362：使用預設送貨地址，而非新送貨地址。
description: 套用ACSD-48362修補程式，修正使用預設送貨地址的Adobe Commerce問題，而非使用可轉讓報價下訂單時的新送貨地址。
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362：使用預設送貨地址，而非新送貨地址

ACSD-48362修補程式修正了使用預設送貨地址，而不是使用可轉讓報價下訂單時新增地址的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48362。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用可轉讓報價下訂單時，會使用預設送貨地址而非新新增的送貨地址。

<u>要再現的步驟</u>：

1. 導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**」以啟用B2B報價。
1. 以公司使用者身分登入。
1. 新增產品至購物車。
1. 前往購物車頁面並請求報價。
1. 移至客戶的&#x200B;**[!UICONTROL My Quotes]**&#x200B;頁面，並選取剛才建立的報價。
1. 移至客戶報價頁面的&#x200B;**[!UICONTROL Shipping Information]**&#x200B;區段。
   * 按一下「**[!UICONTROL Add New Address]**」、填寫表單並儲存地址（請勿選取「**[!UICONTROL Use as my default billing address]**」或「**[!UICONTROL Use as my default shipping address]**」）。
1. 按一下客戶報價頁面上的&#x200B;**[!UICONTROL Send for Review]**。
1. 以管理員使用者身分前往Adobe Commerce管理員，開啟剛建立的報價單，然後按一下&#x200B;**[!UICONTROL Send]**。
1. 現在移至客戶的報價頁面，重新整理頁面，然後按一下&#x200B;**[!UICONTROL Proceed to Checkout]**。
1. 在結帳頁面上，即使已選取新的送貨地址，資料仍會顯示預設送貨地址。
1. 按一下&#x200B;**[!UICONTROL Continue]**&#x200B;並下訂單。

<u>預期結果</u>：

訂單應使用新地址，而不需在結帳頁面上重新選取預設送貨地址。

<u>實際結果</u>：

訂單會以預設送貨地址下單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
