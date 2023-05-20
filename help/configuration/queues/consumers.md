---
title: 消息隊列使用者
description: 瞭解Adobe Commerce和Magento Open Source消息隊列使用者，包括與其關聯的功能和系統配置設定。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---

# 消息隊列使用者

下表標識了所有消息隊列使用者，描述了他們的工作，並標識了與他們關聯的管理系統配置設定：

| 使用者和說明 | Adobe Commerce | Adobe CommerceB2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 為每個任務建立消息 [批量操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)，如導入或導出物料、成批更改價格以及將產品分配給倉庫。 在 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 選項設定為&#x200B;**[!UICONTROL Run asynchronously]**的子菜單。 |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| 在後台非同步生成優惠券。 使用 [批優惠券生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 的子菜單。 |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| 檢查已作為優先順序註冊的事件 [Adobe I/OAdobe Commerce事件](https://developer.adobe.com/commerce/events/get-started/)。 |
| `exportProcessor` | + | + | + |
| 在 [出口](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 大型資料集（例如200,000個產品）。 |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 在下單或產品被刪除後非同步更正股票指數。 在 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 選項。 請參閱 [效能最佳實踐](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update)。 |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 刪除產品時，按產品SKU非同步刪除源項目。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系統配置設定中啟用了stock選項。 |  |  |  |
| `inventory.mass.update` | + | + | + |
| 非同步處理舊庫存物料、更新舊庫存物料、更新預設來源物料和重新索引特定產品SKU的庫存。 在 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 在管理系統配置設定中啟用批量操作。 |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 刪除產品後按產品SKU非同步刪除保留。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系統配置設定中啟用了stock選項。 |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 刪除產品後，按產品SKU非同步更新預留。 在 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 在管理系統配置設定中啟用了stock選項。 |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 非同步更新分配給庫存的每個產品的可售數量。 如果您使用 [!DNL Inventory Management]。 |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| 非同步重新索引源項。 在 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 已設定為「[!UICONTROL asynchronous]」。 |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 非同步重新索引股票。 在 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 已設定為「[!UICONTROL asynchronous]」。 |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 建立臨時資料庫表，移動每個 [客戶細分](https://docs.magento.com/user-guide/marketing/customer-segments.html) 在中，刪除與段ID匹配的所有段，並使用段ID作為指示符將它們複製到客戶段。 這都是在事務中完成的，這樣，如果某事發生故障，事務將回退到執行此操作之前的事務。 事務處理後，使用者將刪除臨時表。 |  |  |  |
| `media.content.synchronization` | + | + | + |
| 確保為產品、類別、CMS塊和CMS頁指定的介質的連結正確分配給資產。 刪除不再使用的舊資產。 |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| 生成並驗證介質資產路徑。 資產的絕對路徑取決於它在伺服器上從媒體目錄內的位置。 映像將調整大小（如有必要）並複製到生成路徑內的媒體目錄。 |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 將映像檔案導入到 `media_gallery_asset` 資料庫表。 |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同步 [調整](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 目錄影像。 |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| 更新可協商報價的價格。 在 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 非同步 [流程訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)，它將訂單標籤為已接收，將其置於消息隊列中，並以先入先出的方式處理它們。 已考慮 [最佳實踐](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 用於改進可處理的訂單數，因為客戶不需要等待後端進程完成後才能看到成功消息。 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 在使用管理員後將更改非同步寫入資料庫中的產品屬性 [更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)。 |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 在使用管理員後，將對資料庫中特定儲存視圖的產品屬性所做的更改非同步寫入資料庫 [更新](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)。 |  |  |  |
| `product_alert` | + | + | + |
| 向客戶發送有關產品價格和庫存更改的通知電子郵件。 當 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 選項。 |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 將採購訂單轉換為 [訂單](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules)。 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 發送採購訂單電子郵件。 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 驗證採購訂單是否與相關 [審批規則](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html)。 在 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 選項。 |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 防止 [問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 一次性優惠券可以多次使用。 |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 更新分配給共用目錄類別的類別。 在 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 更新共用目錄中每個產品的價格。 在 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 選項。 |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 當產品從目錄中刪除或從購物車中刪除時，刪除無效或無效的報價。 在 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 選項。 |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 更新活動購物車以反映購物車價格規則中的更改。 更新時需要 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html)。 |  |  |  |

{style="table-layout:auto"}
