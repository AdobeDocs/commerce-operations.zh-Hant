---
title: 客戶個人資訊參考（版本1.x）
description: 瞭解Magento1.x中客戶個人資訊的資料流和資料庫實體映射。
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# 客戶個人資訊參考（版本1.x）

>[!NOTE]
>
>這是幫助Adobe Commerce和Magento Open Source商家和開發商為遵守隱私法規做準備的一系列主題中的一個。 請咨詢您的法律顧問，以確定您的企業是否以及如何遵守任何法律義務。

在為隱私管理法規開發符合性程式時，請使用以下資料流圖和資料庫實體映射來參考，例如：

- [格德普](gdpr.md)
- [CCPA](ccpa.md)

## 資料流圖

資料流圖顯示了客戶和管理員可以在儲存前端和管理員上輸入和檢索的資料類型。

### 前端資料入口點

用戶在註冊帳戶、結帳期間和類似事件時可以輸入客戶、地址和付款資訊。

![前端資料入口點](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端資料接入點

當客戶登錄並查看多個不同頁面或簽出時，Commerce會載入客戶資訊。

![前端資料接入點](../../assets/security-compliance/frontend-data-access-points.svg)

### 後端資料入口點

商戶可以從管理員輸入客戶、地址和付款資訊以建立客戶或訂單。

![後端資料入口點](../../assets/security-compliance/backend-data-entry-points.svg)

### 後端資料存取點

當商戶查看多種類型的網格、按一下網格以查看詳細資訊以及執行各種其他任務時，Commerce會載入客戶資訊。

![後端資料存取點](../../assets/security-compliance/backend-data-access-points.svg)

## 資料庫實體

Magento1將客戶資訊儲存在客戶、銷售和其他資料庫表中。

### 客戶資料

Magento1將客戶資訊儲存在 `customer_entity` 和 `customer_address_entity` 的下界。 這兩個表都具有幾個可包含自定義客戶屬性的引用表。

#### `customer_entity` 和引用表

中的以下列 `customer_entity`表包含客戶資訊：

| 列 | 資料類型 |
| --- | --- |
| `email` | varchar(255) |

這些表引用 `customer_entity` 並且可以包含自定義客戶屬性：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | 日期 |
| `customer_entity_decimal` | `value` | 十進位(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文本 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` 和引用表

下表引用 `customer_address_entity` 並且可以包含自定義客戶屬性：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | 日期 |
| `customer_address_entity_decimal` | `value` | 十進位(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文本 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 訂單資料

的 `sales_flat_order` 相關表包含客戶名稱、開單地址和發運地址以及相關資訊。

#### `sales_flat_order` 表

中的以下列 `sales_order` 表包含客戶資訊：

| 列 | 資料類型 |
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

#### `sales_flat_order_address` 表

的 `sales_flat_order_address` 表包含客戶地址。

| 列 | 資料類型 |
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
| `vat_id` | 文本 |

#### `sales_flat_order_grid` 表

中的以下列 `sales_flat_order_grid` 表包含客戶資訊：

| 列 | 資料類型 |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` 表

中的以下列 `sales_flat_order_payment` 表包含客戶資訊：

| 列 | 資料類型 |
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

#### `sales_flat_quote` 表

中的以下列 `sales_flat_quote` 表包含客戶資訊：

| 列 | 資料類型 |
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
| `customer_dob` | 日期 |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` 表

中的以下列 `sales_flat_quote_address` 表包含客戶資訊：

| 列 | 資料類型 |
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

#### `sales_flat_quote_payment` 表

的 `sales_flat_quote_payment` 表包括信用卡資訊和其他交易資訊。

| 列 | 資料類型 |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### 存檔資料

以下表和列包含客戶資訊：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 銷售資料

以下表和列包含客戶資訊：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA資料

以下RMA表和列包含客戶資訊：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### 雜項資料

以下表和列包含客戶資訊：

| 表格 | 列 | 資料類型 |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | 文本 |
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
| `persistent_session` | `info` | 文本 |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

其他引用Customer的表：

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
