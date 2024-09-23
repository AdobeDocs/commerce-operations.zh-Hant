---
title: 'ACSD-51574：影像被其他影像取代時未在前端更新'
description: 套用ACSD-51574修補程式，以修正Adobe Commerce將影像取代為其他影像後未在前端更新影像的問題。
feature: Configuration
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-51574：影像被其他影像取代時，前端未更新

ACSD-51574修補程式修正了將影像取代為其他影像後，未在前端更新影像的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-51574。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

以其他影像取代該影像後，前端沒有更新該影像。

<u>要再現的步驟</u>：

1. 建立含有幾個影像的產品。
1. 編輯產品並上傳具有已知名稱的影像（範例： *image.jpg*）。
1. 儲存產品。
1. 再次編輯產品並刪除影像的舊版本，然後上傳具有相同名稱的新版本影像。 **請確定新版本明顯不同，以檢視問題。**
1. 儲存產品。 管理員和前端都會顯示影像。
1. 再次編輯產品並再次重新上傳相同的新影像（使用相同名稱）。
1. 儲存產品並在前端檢查產品頁面。

<u>預期結果</u>：

第二次上傳的影像應為新影像，以及已重新命名的影像名稱。

<u>實際結果</u>：

第二次上傳的影像是先前已刪除的舊版影像，而非相同的新影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
