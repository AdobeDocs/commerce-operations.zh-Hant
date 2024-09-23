---
title: 「ACSD-49822：請購單清單頁面上的更新未反映在列印請購單清單上」
description: 套用ACSD-49822修補程式，以修正請購單清單頁面上的更新未反映在列印請購單清單上的Adobe Commerce問題。
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822：請購單清單的更新未反映在列印請購單清單上

ACSD-49822修補程式修正了請購單清單頁面上的更新未反映在列印請購單清單上的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49822。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

請購單清單頁面上的更新不會反映在列印請購單清單上。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B功能]**&#x200B;以啟用請購單清單。
1. 建立產品。
1. 以客戶身分登入，並將兩個產品新增至請購單清單。
1. 前往&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**。
1. 檢視請購單清單。
1. 按一下右上角的&#x200B;**[!UICONTROL Print]**。
1. 關閉列印視窗並列印請購單清單頁面。
1. 刪除清單中的專案或更新專案數量，然後嘗試再次列印。
1. 您會發現列印視窗上的專案並未更新。
1. 關閉列印視窗。
1. 您會發現請購單清單列印頁面上的料號並未更新。

<u>預期結果</u>：

要列印的清單會在套用任何變更後更新。

<u>實際結果</u>：

更新未反映在請購單清單列印頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
