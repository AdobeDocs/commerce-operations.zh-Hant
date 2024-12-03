---
title: MDVA-44044：將產品指派給新網站後，該產品不會顯示在類別頁面上
description: MDVA-44044修補程式可解決將產品指派給新網站後，產品未顯示在類別頁面上的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16後，即可使用此修補程式。 修補程式ID為MDVA-44044。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044：將產品指派給新網站後，該產品不會顯示在類別頁面上

MDVA-44044修補程式可解決將產品指派給新網站後，產品未顯示在類別頁面上的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16時，即可使用此修補程式。 修補程式ID為MDVA-44044。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品指派給新網站後，不會顯示在類別頁面上。

<u>要再現的步驟</u>：

1. 設定要排程的索引器模式。
1. 建立次要網站、商店和商店檢視。
1. 在`index.php`中新增次要存放區代碼：

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. 建立新類別。
1. 建立指派給新建立類別的新產品。 請確定僅將其指派給主要網站。
1. 執行cron。
1. 從店面開啟類別。
1. 將產品指派至次要網站。
1. 再次執行cron。

<u>預期結果</u>：

產品會在排定的索引器之後出現在類別頁面上。

<u>實際結果</u>：

在完全重新索引之前，產品不會出現在類別頁面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
