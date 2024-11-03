---
title: 新增訊息佇列消費者
description: 瞭解佇列消費者Adobe Systems Commerce 消息，包括與之關聯的功能和系統配置設置。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# 訊息佇列取用者

下表可識別所有訊息佇列使用者、描述其行為，以及識別與其相關的管理員系統組態設定：

| 消費者和說明 | Adobe Commerce | 具有B2B的Adobe Commerce | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 為[大量作業](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)的每個個別工作建立訊息，例如匯入或匯出料號、變更大量價格，以及將產品指定至倉庫。 在管理系統配置設置中將該選項設置為 時&#x200B;**[!UICONTROL Run asynchronously]**&#x200B;為必填。[**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| 以非同步方式在背景產生抵用券。 必須使用[批次抵用券產生](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons)功能。 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| 檢查已在Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/)的[Adobe I/O事件中註冊為優先順序的事件。 |
| `exportProcessor` | + | + | + |
| 防止在大型資料集的[匯出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html)期間發生連線逾時（例如200,000個產品）。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 在下訂單或刪除產品後異步更正股票指數。 在管理員配置設置中啟用該選項時為必填 [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) 。 請參閱 [性能最佳實踐](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update)。 |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 移除產品時，會依產品SKU非同步刪除來源專案。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory)庫存選項時為必要。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| 非同步處理舊庫存專案、更新舊庫存專案、更新預設來源專案，以及重新索引特定產品SKU的存貨。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)大量作業時需要。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 移除產品後，以非同步方式刪除產品SKU的預訂。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory)庫存選項時為必要。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 刪除產品后，按產品SKU異步更新預留。 在管理系統配置設置中啟用庫存選項時 [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) 為必填。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 非同步更新指派給庫存的每種產品的可銷售數量。 如果您使用[!DNL Inventory Management]，此消費者應一律正常運作。 |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| 異步重新索引源項。 當管理系統配置設定中的 設為 「時[!UICONTROL asynchronous]為必填。[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 異步重新索引股票。 當管理系統配置設定中的 設為 「時[!UICONTROL asynchronous]為必填。[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 创建一個臨時数据庫表，將每個 [客戶區段](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) 移動到其中，刪除所有與 區段 ID 匹配的段，並使用區段 ID 作為指示器將它們複製到客戶段。 這一切都是在事務中完成的，因此，如果某些內容失敗，它將事務回滾到執行此事務之前的狀態。 交易之後，消費者會捨棄暫存表格。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 確保產品、類別、CMS區塊和CMS頁面的指派媒體連結已正確指派給資產。 移除不再使用的舊資產。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| 產生并驗證媒體資產路徑。 資產的絕對路徑取決於它在 媒體 目錄中在伺服器上的位置。 圖像大小會重新調整（如有必要）並複製到生成的路徑內的 媒體 目錄。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 將影像檔案 `media_gallery_asset` 匯入資料庫表。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同步[調整](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images)目錄影像的大小。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 更新可轉讓報價的價格。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes)選項時需要。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 異步 [處理訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，將訂單標記為已接收，將它們放在消息佇列中，並以先進先出的方式處理它們。 被認為是 [提高可處理的訂單數量的最佳實務](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) ，因為客戶無需等待後端流程完成即可看到成功消息。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 使用Admin進行[更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)後，以非同步方式將變更寫入資料庫中的產品屬性。 |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 在使用Admin進行[更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)後，以非同步方式將變更寫入資料庫中特定商店檢視的產品屬性。 |                |                         |                     |
| `product_alert` | + | + | + |
| 傳送通知電子郵件給客戶，告知產品價格和存貨變更。 在管理系統組態設定中啟用&#x200B;[**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html)選項時需要。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 將採購單轉換為[訂單](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules)。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html)選項時需要。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 傳送採購訂購電子郵件。 在管理系統配置設置中啟用該選項時 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 為必填。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 根據相關 [審批規則](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules)驗證採購訂單。 在管理系統配置設置中啟用該選項時 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 為必填。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 將儲存工作放入訊息佇列中，即可非同步儲儲存儲存存設定變更，如此可改善包含大量儲存層級設定的部署效能。 必須使用[`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save)模組。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 防止 [一次性優惠券可以多次使用的問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 更新指派給共享目錄類別的類別。 在管理系統配置設置中啟用該選項時 [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) 為必填。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 更新共享目錄中每個產品的價格。 在管理系統配置設置中啟用該選項時 [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) 為必填。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 當產品從目錄中刪除或從購物車中刪除時，刪除無效或非活動報價。 在管理系統配置設置中啟用該選項時 [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) 為必填。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新作用中的購物車以反映購物車價格規則的變更。 更新&#x200B;[**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html)時需要。 |                |                         |                     |

{style="table-layout:auto"}
