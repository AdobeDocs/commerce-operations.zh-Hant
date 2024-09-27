---
title: 'ACSD-58790：修正 [!DNL Chrome]上行動檢視中產品詳細資料頁面影像的夾捏縮放功能'
description: ACSD-58790修正Adobe Commerce問題，亦即 [!DNL Chrome] 上行動檢視中的影像未如預期放大影像。
feature: Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-58790：修正[!DNL Chrome]上行動檢視中產品詳細資料頁面影像的夾捏縮放功能

ACSD-58790修補程式修正Adobe Commerce問題，亦即[!DNL Chrome]上行動檢視中的影像未如預期放大影像。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-58790。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正[!DNL Chrome]上行動檢視中產品詳細資料頁面影像的縮放夾功能。

<u>要再現的步驟</u>：

1. 使用影像建立產品。
1. 從[!DNL Chrome]瀏覽器開啟產品。
1. 按一下影像，然後確認在按兩下時影像會縮放。
1. 使用[!DNL Chrome]開發人員工具切換到行動檢視。
1. 按一下影像。
1. 點兩下。

<u>預期結果</u>：

按兩下時，影像會放大。

<u>實際結果</u>：

按兩下時影像未放大。 此問題特定於行動檢視中的[!DNL Chrome]，因為縮放功能在[!DNL Firefox]中如預期般運作。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
