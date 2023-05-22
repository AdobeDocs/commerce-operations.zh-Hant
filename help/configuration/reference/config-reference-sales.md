---
title: 銷售配置路徑參考
description: 請參閱銷售配置值清單。
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# 銷售配置路徑參考

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **銷售**。

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，它應該在原始碼管理中。 要可選地覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數覆蓋配置設定](override-config-settings.md#environment-variables)。 此主題確實 _不_ 清單 [敏感值和系統特定值](config-reference-sens.md)。

## 銷售路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **銷售**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 隱藏客戶IP | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 折扣 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 裝運 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 稅 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定產品稅 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 總計 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡 | `sales/totals_sort/giftcardaccount` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 儲存信用 | `sales/totals_sort/customerbalance` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許重新排序 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF打印標誌(200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML打印視圖徽標 | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 地址 | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用 | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小金額 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包括稅額 | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 描述消息 | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在購物車中顯示時出錯 | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在多地址簽出中單獨驗證每個地址 | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 多地址說明消息 | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 要在購物車中顯示的多地址錯誤 | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用聚合資料 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 待定付款訂單生存期（分鐘） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許訂單級別上的禮品郵件 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許訂單物料的禮品郵件 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許在訂單層包裝禮品 | `sales/gift_options/wrapping_allow_order` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許訂單物料的禮品包裝 | `sales/gift_options/wrapping_allow_items` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許禮品收據 | `sales/gift_options/allow_gift_receipt` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許打印卡 | `sales/gift_options/allow_printed_card` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 打印卡的預設價格 | `sales/gift_options/printed_card_price` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 啟用MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示實際價格 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設彈出文本消息 | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設「What is This」文本消息 | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面中啟用我的帳戶上按SKU訂購 | `sales/product_sku/my_account_enable` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 按鈕文本 | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客戶組 | `sales/product_sku/allowed_groups` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 啟用存檔 | `sales/magento_salesarchive/active` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已購買的存檔訂單 | `sales/magento_salesarchive/age` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 要存檔的訂單狀態 | `sales/magento_salesarchive/order_statuses` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在店面上啟用RMA | `sales/magento_rma/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在產品層啟用RMA | `sales/magento_rma/enabled_on_product` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 使用儲存地址 | `sales/magento_rma/use_store_address` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 銷售電子郵件路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **銷售電子郵件**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 非同步發送 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單確認電子郵件發件人 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單確認模板 | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的新訂單確認模板 | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送訂單電子郵件複製方法 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訂單注釋電子郵件發件人 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訂單注釋電子郵件模板 | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的訂單注釋電子郵件模板 | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送訂單注釋電子郵件複製方法 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票電子郵件發件人 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票電子郵件模板 | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的發票電子郵件模板 | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送發票電子郵件複製方法 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票注釋電子郵件發件人 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票注釋電子郵件模板 | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的發票注釋電子郵件模板 | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送發票注釋電子郵件複製方法 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運電子郵件發件人 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運電子郵件模板 | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的發運電子郵件模板 | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送發運電子郵件複製方法 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運注釋電子郵件發件人 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運注釋電子郵件模板 | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的發運注釋電子郵件模板 | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送發運注釋電子郵件複製方法 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 貸項通知單電子郵件發件人 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 貸項通知單電子郵件模板 | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的貸項通知單電子郵件模板 | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送貸項通知單電子郵件複製方法 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 貸項通知單注釋電子郵件發件人 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 貸項通知單注釋電子郵件模板 | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的貸項通知單注釋電子郵件模板 | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送貸項通知單備注電子郵件複製方法 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/magento_rma/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA電子郵件發送方 | `sales_email/magento_rma/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA電子郵件模板 | `sales_email/magento_rma/template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA電子郵件模板 | `sales_email/magento_rma/guest_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 發送RMA電子郵件複製方法 | `sales_email/magento_rma/copy_method` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_auth/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA授權電子郵件發送程式 | `sales_email/magento_rma_auth/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA授權電子郵件模板 | `sales_email/magento_rma_auth/template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA授權電子郵件模板 | `sales_email/magento_rma_auth/guest_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 發送RMA授權電子郵件複製方法 | `sales_email/magento_rma_auth/copy_method` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_comment/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA注釋電子郵件發送方 | `sales_email/magento_rma_comment/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA注釋電子郵件模板 | `sales_email/magento_rma_comment/template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA注釋電子郵件模板 | `sales_email/magento_rma_comment/guest_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 發送RMA電子郵件複製方法 | `sales_email/magento_rma_comment/copy_method` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_customer_comment/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA注釋電子郵件發送方 | `sales_email/magento_rma_customer_comment/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA注釋電子郵件收件人 | `sales_email/magento_rma_customer_comment/recipient` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| RMA注釋電子郵件模板 | `sales_email/magento_rma_customer_comment/template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 發送RMA電子郵件複製方法 | `sales_email/magento_rma_customer_comment/copy_method` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在標題中顯示訂單ID | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在標題中顯示訂單ID | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在標題中顯示訂單ID | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 稅道

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **稅**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 發運的稅分類 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品選項的稅分類 | `tax/classes/wrapping_tax_class` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 產品的預設稅分類 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客戶的預設稅分類 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基於的計稅方法 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基於 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目錄價格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 裝運價格 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 應用客戶稅 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 對價格應用折扣 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 應用稅 | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用跨境貿易 | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設國家/地區 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設狀態 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設帖子代碼 | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在目錄中顯示產品價格 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示發運價格 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示價格 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示小計 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示發運金額 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示禮品包裝價格 | `tax/cart_display/gift_wrapping` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 顯示打印的卡價格 | `tax/cart_display/printed_card` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在訂單中包括稅合計 | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示完整納稅匯總 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示零稅小計 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示價格 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示小計 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示發運金額 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示禮品包裝價格 | `tax/sales_display/gift_wrapping` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 顯示打印的卡價格 | `tax/sales_display/printed_card` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在訂單中包括稅合計 | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示完整納稅匯總 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示零稅小計 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在產品清單中顯示價格 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在「產品視圖」頁上顯示價格 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在銷售模組中顯示價格 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在電子郵件中顯示價格 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 對FPT應用稅 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在小計中包括FPT | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 簽出路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **簽出**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用Onepage簽出 | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許來賓簽出 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示開單地址 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用條款和條件 | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 報價生命週期（天） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 添加產品後重定向到購物車 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已分組的產品映像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可配置產品映像 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預覽報價生命週期（分鐘） | `checkout/cart/preview_quota_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 顯示購物車摘要 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示購物車邊欄 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近添加的項的最大顯示數 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗電子郵件發件人 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗電子郵件接收器 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗模板 | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送付款失敗的電子郵件複製方法 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 裝運設定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **裝運設定**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 應用自定義發運策略 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 裝運策略 | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 多裝運設定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **多發送設定**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 允許發運至多個地址 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許發運至多個地址的最大數量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 傳遞方法路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **傳遞方法**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 已啟用 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 類型 | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 價格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂單金額 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 條件 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在價格計算中包括虛擬產品 | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 導出 | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 導入 | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用簽出 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為RMA啟用 | `carriers/ups/active_rma` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| UPS類型 | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 模式 | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 裝運原點 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 網關URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用協定費率 | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包請求類型 | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目標類型 | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裝重量（請咨詢您的運輸承運人，瞭解最大支援的運輸重量） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拾取方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小包裝重量（請咨詢您的運輸承運人，瞭解最小支援的運輸重量） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已應用處理 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費發運閾值 | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免費發運金額閾值 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用簽出 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為RMA啟用 | `carriers/usps/active_rma` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 模式 | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包請求類型 | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 長度 | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬度 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 吉爾特 | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可加工 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裝重量（請咨詢您的運輸承運人，瞭解最大支援的運輸重量） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已應用處理 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費發運閾值 | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免費發運金額閾值 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 調試 | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用簽出 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為RMA啟用 | `carriers/fedex/active_rma` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 標題 | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服務URL（生產） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服務URL（沙盒） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包請求類型 | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包裝 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 德羅波夫 | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裝重量（請咨詢您的運輸承運人，瞭解最大支援的運輸重量） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已應用處理 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住宅交付 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 集線器ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費發運閾值 | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免費發運金額閾值 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 調試 | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用簽出 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為RMA啟用 | `carriers/dhl/active_rma` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 標題 | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 內容類型 | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已應用處理 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 分階權重 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 深度 | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬度 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 就緒時間 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤消息 | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費發運閾值 | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免費發運金額閾值 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至適用國家/地區 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發運至特定國家 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果不適用，則顯示方法 | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## GoogleAPI路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **GoogleAPI**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用 | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 帳戶類型 | `google/analytics/type` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 啟用內容實驗 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目錄頁的清單屬性 | `google/analytics/catalog_page_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 交叉銷售塊的清單屬性 | `google/analytics/crosssell_block_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 追加銷售塊的清單屬性 | `google/analytics/upsell_block_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 相關產品塊的清單屬性 | `google/analytics/related_block_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 搜索結果頁的清單屬性 | `google/analytics/search_page_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 促銷欄位「標籤」的「內部促銷」。 | `google/analytics/promotions_list_value` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 啟用 | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換語言 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換格式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換顏色 | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換標籤 | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換值類型 | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換值 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 禮品卡路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **禮品卡**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 禮品卡通知電子郵件發件人 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡通知電子郵件模板 | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可贖回 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生存期（天） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許禮品消息 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品消息最大長度 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在訂單項為時生成禮品卡帳戶 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡電子郵件發件人 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡模板 | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼長度 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼格式 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼前置詞 | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼尾碼 | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每X個字元划線 | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新建池大小 | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低代碼池閾值 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
