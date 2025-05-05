---
title: ACSD-50621：看不到共用目錄中不同網站的分層價格
description: 套用ACSD-50621修補程式，修正共用目錄中不同網站在多網站環境中編輯時，無法顯示其層級價格的Adobe Commerce問題。
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621：看不到共用目錄中不同網站的分層價格

ACSD-50621修補程式修正了在多網站環境中編輯共用目錄中不同網站的層級價格時，無法顯示這些網站的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-50621。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在多網站環境中編輯共用目錄中不同網站的層級價格時，不會顯示這些網站的層級價格。

<u>要再現的步驟</u>：

1. 將&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;設為&#x200B;**[!UICONTROL Website]**。
1. 建立其他網站、商店和商店評論。
1. 建立簡單的產品並將其指派給所有網站。
1. 建立自訂共用目錄。
1. 移至&#x200B;**[!UICONTROL Set Pricing and Structure]**&#x200B;以取得您建立的自訂共用目錄。
1. 在步驟1：選取目錄的產品。 新增您建立的簡單產品。
1. 步驟2：設定自訂價格並按一下&#x200B;**[!UICONTROL Configure]**。
1. 針對不同的網站設定不同的層級價格。
1. 選取&#x200B;**[!UICONTROL Done]**&#x200B;並按一下&#x200B;**[!UICONTROL Generate Catalog]**，然後按一下&#x200B;**[!UICONTROL Save]**。
1. 執行cron。
1. 導覽至&#x200B;**[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]**，然後驗證層級價格。

<u>預期結果</u>：

所有先前針對不同網站設定的層級價格都會呈現。

<u>實際結果</u>：

先前設定的層級價格不存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
