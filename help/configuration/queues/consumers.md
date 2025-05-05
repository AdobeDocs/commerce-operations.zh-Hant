---
title: 訊息佇列取用者
description: 瞭解Adobe Commerce訊息佇列使用者，包括與其相關的功能和系統組態設定。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# 訊息佇列取用者

下表可識別所有訊息佇列使用者、描述其行為，以及識別與其相關的管理員系統組態設定：

| 消費者和說明 | Adobe Commerce | 具有B2B的Adobe Commerce | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 為[大量作業](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)的每個個別工作建立訊息，例如匯入或匯出料號、變更大量價格，以及將產品指定至倉庫。 當Admin系統組態設定中的&#x200B;[**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)選項設為&#x200B;**[!UICONTROL Run asynchronously]**&#x200B;時為必要。 |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| 以非同步方式在背景產生抵用券。 必須使用[批次抵用券產生](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html?lang=zh-Hant#method-2%3A-generate-a-batch-of-coupons)功能。 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| 檢查已在Adobe Commerce[&#128279;](https://developer.adobe.com/commerce/events/get-started/)的Adobe I/O事件中註冊為優先順序的事件。 |
| `exportProcessor` | + | + | + |
| 防止在大型資料集的[匯出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html?lang=zh-Hant)期間發生連線逾時（例如200,000個產品）。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 下訂單或移除產品後，以非同步方式修正股票指數。 在管理員組態設定中啟用&#x200B;[**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory#product-stock-options)選項時需要。 請參閱[效能最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html?lang=zh-Hant#deferred-stock-update)。 |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 移除產品時，會依產品SKU非同步刪除來源專案。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory)庫存選項時為必要。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| 非同步處理舊庫存專案、更新舊庫存專案、更新預設來源專案，以及重新索引特定產品SKU的存貨。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)大量作業時需要。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 移除產品後，以非同步方式刪除產品SKU的預訂。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory)庫存選項時為必要。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 移除產品後，以非同步方式更新產品SKU的預訂。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory)庫存選項時為必要。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 非同步更新指派給庫存的每種產品的可銷售數量。 如果您使用[!DNL Inventory Management]，此消費者應一律正常運作。 |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| 以非同步方式重新索引來源專案。 當Admin系統組態設定中的&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)設為&quot;[!UICONTROL asynchronous]&quot;時需要。 |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 以非同步方式重新索引庫存。 當Admin系統組態設定中的&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)設為&quot;[!UICONTROL asynchronous]&quot;時需要。 |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 建立暫存資料庫表格、將每個[客戶區段](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/customers/segments/customer-segments)移入其中、刪除符合區段ID的所有區段，並使用區段ID作為指標將其複製到客戶區段。 這些操作都會在交易中完成，因此如果某個專案失敗，就會將交易復原到執行此動作之前的狀態。 交易之後，消費者會捨棄暫存表格。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 確保產品、類別、CMS區塊和CMS頁面的指派媒體連結已正確指派給資產。 移除不再使用的舊資產。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| 產生並驗證媒體資產路徑。 資產的絕對路徑取決於它從媒體目錄內位於伺服器上的位置。 影像會重新調整大小（如有必要），並複製到產生路徑內的媒體目錄中。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 將影像檔案匯入`media_gallery_asset`資料庫資料表。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同步[調整](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images)目錄影像的大小。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 更新可轉讓報價的價格。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/quotes/quotes)選項時需要。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 非同步[處理訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，將訂單標示為已接收、將其放入訊息佇列，並以先進先出方式處理。 改善可處理訂單數的[最佳實務](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md)，因為客戶不需要等待後端程式完成才能看到成功訊息。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 使用Admin進行[更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=zh-Hant)後，以非同步方式將變更寫入資料庫中的產品屬性。 |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 在使用Admin進行[更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=zh-Hant)後，以非同步方式將變更寫入資料庫中特定商店檢視的產品屬性。 |                |                         |                     |
| `product_alert` | + | + | + |
| 傳送通知電子郵件給客戶，告知產品價格和存貨變更。 在管理系統組態設定中啟用&#x200B;[**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html?lang=zh-Hant)選項時需要。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 將採購單轉換為[訂單](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules)。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=zh-Hant)選項時需要。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 傳送採購單電子郵件。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=zh-Hant)選項時需要。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 依據相關[核准規則](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules)驗證採購單。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=zh-Hant)選項時需要。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 將儲存工作放入訊息佇列中，即可非同步儲儲存儲存存設定變更，如此可改善包含大量儲存層級設定的部署效能。 必須使用[`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save)模組。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 避免單次使用抵用券多次使用的問題。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 更新指派給共用目錄類別的類別。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)選項時需要。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 更新共用目錄中每個產品的價格。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)選項時需要。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 當產品從目錄中刪除或從購物車中移除時，會刪除無效或無效的報價單。 在系統管理員組態設定中啟用&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/quotes/quotes)選項時需要。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新作用中的購物車以反映購物車價格規則的變更。 更新&#x200B;[**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html?lang=zh-Hant)時需要。 |                |                         |                     |

{style="table-layout:auto"}
