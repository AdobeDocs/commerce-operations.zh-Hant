---
title: ACSD-52219：解決書籤檢視切換中的管理員格線篩選問題
description: 套用ACSD-52219修補程式，修正Adobe Commerce中當經常在書籤檢視之間切換時，管理員格線的已儲存篩選器無法正常運作的問題。
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219：解決書籤檢視切換中的管理員格線篩選問題

ACSD-52219修補程式修正經常在書籤檢視之間切換時，管理員格線的已儲存篩選器無法正常運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-52219。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當經常在書籤檢視之間切換時，管理格線中儲存的篩選器無法如預期運作。

<u>要再現的步驟</u>：

1. 存取Admin中的[!DNL Sales Order]網格。
1. 建立兩到三個篩選器。
1. 切換檢視以驗證篩選器設定，確保它們已正確儲存。
1. 前往篩選器1或篩選器2。
1. 重新整理頁面以更新顯示的資料。
1. 切換到不同的檢視，並注意篩選條件保持不變。
1. 請注意，預設檢視現在會顯示篩選的結果，即使未設定特定的篩選條件亦然。

<u>預期結果</u>：

這些篩選器不會交換並保留其原始狀態。

<u>實際結果</u>：

修改檢視時，篩選器會混合在一起，且未儲存正確的檢視。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
