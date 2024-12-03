---
title: ACSD-56979：刪除中繼更新後移除的產品影像
description: 套用ACSD-56979修補程式以修正Adobe Commerce問題，此問題導致刪除中繼更新後會移除產品影像
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979：刪除中繼更新後移除的產品影像

ACSD-56979修補程式修正刪除中繼更新後移除產品影像的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-56979。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce和Magento Open Source版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

刪除中繼更新後會移除產品影像。

<u>要再現的步驟</u>：

1. 在Commerce管理側邊欄上，前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;並建立產品。
1. 在&#x200B;**[!UICONTROL Images and Videos]**&#x200B;底下，上傳影像並儲存產品。
1. 在&#x200B;**[!UICONTROL Scheduled Changes]**&#x200B;方塊中，選取&#x200B;**[!UICONTROL Schedule New Update]**。
   1. 選擇未來幾分鐘的開始日期。
   1. 請勿選擇結束日期。
1. 在&#x200B;**[!UICONTROL Scheduled Changes]**&#x200B;方塊中，選取&#x200B;**[!UICONTROL View/Edit]**&#x200B;連結。
1. 前往&#x200B;**[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]**&#x200B;並選取&#x200B;**[!UICONTROL Done]**。
1. 重新整理頁面。

<u>預期結果</u>：

由於更新會在排定的開始日期之前移除，因此產品應保持不變。

<u>實際結果</u>：

影像內容會遺失並顯示零位元組。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
