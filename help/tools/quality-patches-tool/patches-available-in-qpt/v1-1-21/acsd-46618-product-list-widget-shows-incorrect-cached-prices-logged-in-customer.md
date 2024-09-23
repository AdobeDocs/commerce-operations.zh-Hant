---
title: 「ACSD-46618：產品清單Widget針對登入的客戶顯示不正確的快取價格」
description: 套用修補程式，修正Adobe Commerce產品清單Widget對登入客戶顯示錯誤快取價格的問題。
feature: Cache, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46618：產品清單Widget針對登入的客戶顯示不正確的快取價格

ACSD-46618修補程式解決產品清單Widget針對登入客戶顯示不正確快取價格的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46618。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

ACSD-46618修補程式解決產品清單Widget針對登入客戶顯示不正確快取價格的問題。

<u>要再現的步驟</u>：

1. 在Adobe Commerce Admin中，依序選取&#x200B;**[!UICONTROL Stores]**、**[!UICONTROL Configuration]**、展開&#x200B;**[!UICONTROL Sales]**，然後選取&#x200B;**[!UICONTROL Tax]**。 更新稅捐設定以顯示含稅與不含稅的價格。
1. 設定&#x200B;**[!UICONTROL Enable Cross Border Trade]** = _是_。
1. 建立只適用於美國的稅捐規則。
1. 將Widget新增至包含多項產品的首頁。
1. 建立兩個具有美國地址和非美國地址的客戶。
1. 從店面使用美國客戶登入。 請確定已快取頁面。
1. 觀察首頁Widget中顯示的價格。
1. 登出並使用非美國客戶登入。

<u>預期結果</u>：

首頁Widget中顯示的價格會與客戶地址相對應。

<u>實際結果</u>：

首頁Widget會顯示非美國客戶使用稅捐的價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
