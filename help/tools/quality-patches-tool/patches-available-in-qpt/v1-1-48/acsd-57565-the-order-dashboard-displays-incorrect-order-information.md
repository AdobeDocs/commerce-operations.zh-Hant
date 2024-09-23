---
title: 'ACSD-57565：訂單儀表板顯示不正確的訂單資訊'
description: 套用ACSD-57565修補程式，修正Adobe Commerce訂單控制面板在更新時段前顯示錯誤訂單資訊的問題。
feature: Roles/Permissions
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-57565：訂單儀表板顯示不正確的訂單資訊

ACSD-57565修補程式修正了訂單控制面板在更新時段前顯示錯誤訂單資訊的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-57565。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式

## 問題

訂單儀表板顯示不正確的訂單資訊。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL dashboard charts]**。
1. 建立訂單並開立商業發票。
1. 建立訂單後，請至少等待24小時。
1. 檢查&#x200B;**[!UICONTROL dashboard chart]**&#x200B;資料。
1. 記下完整的訂單計數。
1. 將時間變更為&#x200B;*目前月份*，然後再變更回&#x200B;*今天*。

<u>預期結果</u>：

儀表板圖表應始終顯示正確的統計資料。

<u>實際結果</u>：

儀表板圖表在第一次載入時顯示不正確的統計資料。 圖表的精確統計資料會在時段之後更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
