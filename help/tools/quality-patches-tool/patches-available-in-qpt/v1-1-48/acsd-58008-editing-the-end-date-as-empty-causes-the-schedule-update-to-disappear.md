---
title: 'ACSD-58008：將結束日期編輯為*empty*會導致排程更新消失'
description: 套用ACSD-58008修補程式以修正Adobe Commerce將結束日期編輯為*empty*會導致排程更新消失的問題。
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008：將結束日期編輯為&#x200B;*empty*&#x200B;會導致排程更新消失

ACSD-58008修補程式修正將結束日期編輯為&#x200B;*empty*&#x200B;會導致排程更新消失的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-58008。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將結束日期編輯為&#x200B;*empty*&#x200B;會導致排程更新消失

<u>要再現的步驟</u>：

1. 以[!UICONTROL Admin]登入。
1. 前往「**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**」並建立頁面。
1. 選取已建立的頁面，然後按一下&#x200B;**[!UICONTROL Schedule New Update]**。 *（在頁面的右上角導覽）*。
1. 建立四個更新。 *（例如，以* 2 *分鐘為增量）*。
1. 更新&#x200B;*更新2*，並將時間變更為最後一個&#x200B;*更新4*&#x200B;之前的時間。
1. 儲存所做的更新。

<u>預期結果</u>：

排程更新顯示&#x200B;*更新3*。

<u>實際結果</u>：

排程更新未顯示&#x200B;*更新3*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
