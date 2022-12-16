---
title: 消息隊列使用者
description: 了解Adobe Commerce和Magento Open Source訊息佇列使用者，包括相關功能和系統組態設定。
source-git-commit: 2eecaab32b090cfd3c1a8e8832027d3531cf0edc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 消息隊列使用者

下表標識所有消息隊列使用者，描述他們的工作，並標識與他們關聯的管理系統配置設定：

| 消費者和說明 | Adobe Commerce | Adobe Commerce與B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 為 [批量操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)，例如導入或導出物料、更改成批量價格以及將產品分配給倉庫。 若 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 選項設為&#x200B;**[!UICONTROL Run asynchronously]**（在管理系統配置設定中）。 |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| 非同步在背景產生抵用券。 使用 [批次抵用券產生](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 功能。 |  |  |  |
| `exportProcessor` | + | + | + |
| 在 [匯出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 大型資料集（例如200,000個產品）。 |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 在下訂單或刪除產品後，非同步更正股指。 若 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 選項。 請參閱 [效能最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 移除產品時，會依產品SKU非同步刪除來源項目。 若 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中會啟用「庫存」選項。 |  |  |  |
| `inventory.mass.update` | + | + | + |
| 非同步處理舊庫存項目、更新舊庫存項目、更新預設來源項目，以及重新索引特定產品SKU的庫存。 若 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 在管理系統配置設定中啟用批量操作。 |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 移除產品後，依產品SKU以非同步方式刪除保留。 若 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中會啟用「庫存」選項。 |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 移除產品後，會依產品SKU以非同步方式更新保留。 若 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 系統組態設定中會啟用「庫存」選項。 |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 以非同步方式更新分配給庫存的每種產品的可銷售數量。 如果您使用 [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| 非同步地重新索引源項。 若 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 設為「[!UICONTROL asynchronous]「 」（在管理系統配置設定中）。 |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 非同步地重新索引庫存。 若 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 設為「[!UICONTROL asynchronous]「 」（在管理系統配置設定中）。 |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 建立臨時資料庫表，移動每個表 [客戶區段](https://docs.magento.com/user-guide/marketing/customer-segments.html) 刪除與區段ID相符的所有區段，並以區段ID作為指標，將其複製至客戶區段。 這都是在交易中完成的，因此，如果某件事件失敗，它會將交易回滾到執行此操作之前的狀態。 交易後，使用者會捨棄臨時表格。 |  |  |  |
| `media.content.synchronization` | + | + | + |
| 確保為產品、類別、CMS區塊和CMS頁面指派的媒體連結正確指派給資產。 移除已不再使用的舊資產。 |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| 產生並驗證媒體資產路徑。 資產的絕對路徑取決於資產從媒體目錄內置於伺服器上的位置。 影像會調整大小（如有必要），並複製到產生路徑內的媒體目錄。 |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 將影像檔案匯入至 `media_gallery_asset` 資料庫表。 |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同步 [調整](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 目錄影像。 |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| 更新可轉讓報價的價格。 若 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 非同步 [處理訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，會將訂單標示為已接收，將其置於訊息佇列中，並以先入先出的方式處理。 被視為 [最佳實務](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 以改善可處理的訂單數，因為客戶不需要等待後端程式完成後才看到成功訊息。 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 使用管理員後，以非同步方式將變更寫入資料庫中的產品屬性 [更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 使用管理員後，以非同步方式將變更寫入資料庫中特定商店檢視的產品屬性中 [更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| 傳送有關產品價格和存貨變更的通知電子郵件給客戶。 必要時，若 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 選項。 |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 將採購訂單轉換為 [訂購](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 若 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 傳送採購訂單電子郵件。 若 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 根據相關條件驗證採購訂單 [核准規則](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 若 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 防止 [問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 可多次使用一次性抵用券。 |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 更新分配給共用目錄類別的類別。 若 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 更新共用目錄中每個產品的價格。 若 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 從目錄中刪除或從購物車中移除產品時，刪除無效或非作用中的報價。 若 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |

{style=&quot;table-layout:auto&quot;}
