---
title: 'MDVA-39711：刪除網站後無法存取客戶方格'
description: MDVA-39711修補程式修正管理員使用者在刪除網站後無法存取客戶網格的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 修補程式ID為MDVA-39711。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: Configuration
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39711：刪除網站後無法存取客戶網格

MDVA-39711修補程式修正管理員使用者在刪除網站後無法存取客戶網格的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 修補程式ID為MDVA-39711。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.7-p2、2.3.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者在刪除網站後無法存取客戶的網格。

<u>要再現的步驟</u>：

1. 建立新網站、商店和商店檢視。
1. 在管理員上建立新客戶，並將其與建立的網站建立關聯。
1. 移至&#x200B;**商店** > **所有商店**，並刪除已建立的網站。
1. 移至&#x200B;**客戶** > **所有客戶**。

<u>預期結果</u>：

* 沒有錯誤訊息。
* 所有客戶都會顯示在格線中。

<u>實際結果</u>：

* 使用者收到錯誤訊息： *找不到所要求的ID 2網站。 請驗證網站，然後再試一次*
* 所有客戶都不會顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。