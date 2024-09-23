---
title: 'MDVA-38799：建立中繼更新後未儲存可下載的產品'
description: MDVA-38799修補程式可解決建立中繼更新後無法儲存可下載產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-38799。 請注意，Adobe Commerce 2.4.3版已修正問題。
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799：建立中繼更新後未儲存可下載的產品

MDVA-38799修補程式可解決建立中繼更新後無法儲存可下載產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-38799。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立中繼更新後，不會儲存可下載的產品。 使用者收到錯誤訊息： *可下載的範例與產品無關。 請驗證連結，然後再試一次*。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;**目錄** > **產品**。
1. 按一下「新增產品」旁的下拉式清單，然後選取「可下載的產品」。
   * 填寫產品的名稱、SKU、價格及數量。
1. 向下捲動至「可下載的資訊」頁面。
1. 在範例底下，按一下&#x200B;**新增連結**。
   * 填寫標題，上傳檔案（檔案型別不重要）。
1. 按一下&#x200B;**儲存**。 您將會收到下列訊息： *您儲存了產品*。
1. 按一下頁面頂端的&#x200B;**排程新更新**。
   * 填寫「更新名稱」，以及合法的「開始日期」和「結束日期」。
1. 在中繼更新上按一下&#x200B;**儲存**。
1. 按一下產品上的&#x200B;**儲存**。

<u>預期結果</u>：

產品已儲存且無任何錯誤。

<u>實際結果</u>：

您收到錯誤訊息： *可下載的範例與產品無關。 請驗證連結，然後再試一次*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
