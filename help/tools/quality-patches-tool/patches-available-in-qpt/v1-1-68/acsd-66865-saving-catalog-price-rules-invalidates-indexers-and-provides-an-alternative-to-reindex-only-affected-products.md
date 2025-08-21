---
title: ACSD-66865：儲存[!UICONTROL Catalog Price Rule]會使索引子失效，並提供僅重新索引受影響產品的替代方式
description: 套用ACSD-66865修補程式以修正Adobe Commerce問題，其中  儲存[!UICONTROL Catalog Price Rules]會使索引子失效，並提供僅重新索引受影響產品的替代方式。
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865：儲存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;會使索引子失效，並提供僅重新索引受影響產品的替代方式

The ACSD-66865 patch fixes the issue where saving a **[!UICONTROL Catalog Price Rule]** invalidates indexers and provides an alternative to reindex only affected products. 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 The patch ID is ACSD-66865. 請注意，此問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Saving a **[!UICONTROL Catalog Price Rule]** causes all indexers to be invalidated, triggering full reindexes instead of reindexing only affected products.

<u>要再現的步驟</u>：

1. Ensure cron isn&#39;t running and all indexers are set to update on schedule (except `customer_grid` which can update on save).
2. Run a full manual reindex using the command: `php bin/magento indexer:reindex`.
3. Verify all indexes show status *[!UICONTROL Ready]* with *0* items in the backlog.
4. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**。 Create an active catalog price rule for a single product (for example, using a *SKU* condition).
5. Run the command: `php bin/magento indexer:status` to check indexer status.
6. 請注意，即使只有一個產品受到影響，多個索引仍會標示為&#x200B;**[!UICONTROL Reindex Required]**。

<u>預期結果</u>：

僅會識別受影響的產品資料，並觸發部分重新索引，而非所有索引器的完整重新索引。

<u>實際結果</u>：

A full reindex is triggered for all indexers, even when only a single product is affected by the **[!UICONTROL Catalog Price Rule]**.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
