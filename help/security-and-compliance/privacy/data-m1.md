---
title: 客戶個人資訊參考（1.x版）
description: 了解Magento1.x中客戶個人資訊的資料流和資料庫實體映射。
source-git-commit: 2120e5bb912a89c58611ef9e23661a54e40a14f1
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---


# 客戶個人資訊參考（1.x版）

>[!NOTE]
>
>這是一系列主題中的一個，可協助Adobe Commerce和Magento Open Source商與開發人員準備遵守隱私權法規。 請洽詢您的法律顧問，以判斷您的企業是否應遵守及如何遵守任何法律義務。

為隱私管理法規開發合規性程式時，請使用以下資料流圖表和資料庫實體映射作為參考，例如：

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 資料流圖

資料流圖表顯示客戶和管理員可以在店面和管理員中輸入和檢索的資料類型。

### 前端資料入口點

用戶在註冊帳戶、結帳期間和類似事件時可以輸入客戶、地址和付款資訊。

![前端資料入口點](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端資料接入點

客戶登入並檢視數個不同頁面或結帳時，商務會載入客戶資訊。

![前端資料接入點](../../assets/security-compliance/frontend-data-access-points.svg)

### 後端資料入口點

商家可以從管理員輸入客戶、地址和付款資訊以建立客戶或訂單。

![後端資料入口點](../../assets/security-compliance/backend-data-entry-points.svg)

### 後端資料存取點

當商戶檢視數種格線、按一下格線以查看詳細資訊，以及執行各種其他工作時，商務會載入客戶資訊。

![後端資料存取點](../../assets/security-compliance/backend-data-access-points.svg)

## 資料庫實體

Magento1將客戶資訊儲存在客戶、銷售和其他資料庫表中。

### 客戶資料

Magento1將客戶資訊儲存在 `customer_entity` 和 `customer_address_entity` 表格。 這兩個表格都有數個可包含自訂客戶屬性的參考表格。

#### `customer_entity` 和引用表

以下欄位位於 `customer_entity`表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `email` | varchar(255) |

這些表引用 `customer_entity` 可包含自訂客戶屬性：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | 日期時間 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文字 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` 和引用表

下表參考 `customer_address_entity` 可包含自訂客戶屬性：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | 日期時間 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文字 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 訂購資料

此 `sales_flat_order` 相關表格包含客戶的名稱、帳單和運送地址以及相關資訊。

#### `sales_flat_order` 表格

以下欄位位於 `sales_order` 表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` 表格

此 `sales_flat_order_address` 表格包含客戶的地址。

| 欄 | 資料類型 |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | 文字 |

#### `sales_flat_order_grid` 表格

以下欄位位於 `sales_flat_order_grid` 表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` 表格

以下欄位位於 `sales_flat_order_payment` 表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### 報價資料

報價包含客戶的姓名、電子郵件、地址和相關資訊。

#### `sales_flat_quote` 表格

以下欄位位於 `sales_flat_quote` 表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | 日期時間 |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` 表格

以下欄位位於 `sales_flat_quote_address` 表格包含客戶資訊：

| 欄 | 資料類型 |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment` 表格

此 `sales_flat_quote_payment` 表包括信用卡資訊和其他交易資訊。

| 欄 | 資料類型 |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### 封存資料

下表和列包含客戶資訊：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 銷售資料

下表和列包含客戶資訊：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA資料

以下RMA表和列包含客戶資訊：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### 其他資料

下表和列包含客戶資訊：

| 表格 | 欄 | 資料類型 |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | 文字 |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | 文字 |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

參考客戶的其他表：

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
