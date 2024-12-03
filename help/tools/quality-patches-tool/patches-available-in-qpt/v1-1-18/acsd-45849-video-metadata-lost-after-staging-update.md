---
title: ACSD-45849：中繼更新後視訊中繼資料遺失
description: ACSD-45849修補程式修正了套用測試更新後視訊中繼資料遺失的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18後，即可使用此修補程式。 修補程式ID為ACSD-45849。 請注意，問題已在Adobe Commerce 2.4.4中修正。
feature: Staging, Page Content
role: Admin
exl-id: cbab0120-585a-47ef-8ed9-abb2da1ec3d6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849：中繼更新後視訊中繼資料遺失

ACSD-45849修補程式修正了套用測試更新後視訊中繼資料遺失的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18時，即可使用此修補程式。 修補程式ID為ACSD-45849。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用中繼更新後，視訊中繼資料會遺失。

<u>要再現的步驟</u>：

1. 在&#x200B;**管理員** > **商店** > **設定** > **目錄** > **產品影片**&#x200B;中設定YouTube API金鑰。
1. 使用YouTube影片建立產品。 請注意，系統會填寫URL、標題和說明。
1. 使用任何引數為產品建立新的排程更新，而不變更&#x200B;*影像和視訊*&#x200B;區段。
1. 按一下排程變更中的&#x200B;**檢視/編輯**。
1. 移至&#x200B;**影像和影片**，然後按一下影片。

<u>預期結果</u>：

URL、標題和說明包含適當的資料。

<u>實際結果</u>：

URL、標題和說明欄位是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
