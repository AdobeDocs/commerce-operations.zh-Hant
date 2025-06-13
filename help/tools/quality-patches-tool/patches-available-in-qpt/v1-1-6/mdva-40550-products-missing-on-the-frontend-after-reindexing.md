---
title: MDVA-40550：重新索引後前端上遺失的產品
description: MDVA-40550修補程式可解決重新索引導致部分或全部店麵類別遺失產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40550。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550：重新索引後前端上遺失的產品

MDVA-40550修補程式可解決重新索引導致部分或全部店麵類別遺失產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40550。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立產品。
1. 將索引子切換為&#x200B;**依排程**&#x200B;更新。
   * 將產品指派至類別。
1. 啟用xdebug並在`\Magento\Indexer\Model\Indexer::reindexAll`和`\Magento\Indexer\Model\IndexMutex::execute`中建立xdebug中斷點。
1. 使用下列命令執行`catalog_category_product`的&#x200B;**完整重新索引**：

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * 等候執行在中斷點`\Magento\Indexer\Model\Indexer::reindexAll`停止。

1. 在另一個主控台中，使用下列命令並行執行&#x200B;**部分重新索引**：

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 等候執行在中斷點`\Magento\Indexer\Model\IndexMutex::execute`停止。 它會鎖定`catalog_category_product`索引子。
1. 繼續執行`catalog_category_product`的完整重新索引，並等候鎖定逾時（60秒）。

<u>預期結果</u>：

主控台中沒有錯誤訊息。

<u>實際結果</u>：

您會收到下列錯誤：

*無法取得索引的鎖定： catalog_category_product。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
