---
title: 客戶個人資訊參考（2.x版）
description: 瞭解Adobe Commerce和Magento Open Source2.x中客戶個人資訊的資料流圖和資料庫實體映射。
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 客戶個人資訊參考（2.x版）

>[!NOTE]
>
>這是幫助Adobe Commerce和Magento Open Source商家和開發商為遵守隱私法規做準備的一系列主題中的一個。 請咨詢您的法律顧問，以確定您的企業是否以及如何遵守任何法律義務。

在為隱私管理法規開發符合性程式時，請使用以下資料流圖和資料庫實體映射來參考，例如：

- [格德普](gdpr.md)
- [CCPA](ccpa.md)

## 資料流圖

資料流圖顯示了客戶和管理員可以輸入和從儲存前端和管理員檢索的資料類型。

### 前端資料入口點

用戶在註冊帳戶、結帳期間和類似事件時可以輸入客戶、地址和付款資訊。

![前端資料入口點](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端資料接入點

Adobe Commerce和Magento Open Source在客戶登錄並查看多個不同頁面或簽出時載入客戶資訊。

![前端資料接入點](../../assets/security-compliance/frontend-data-access-points.svg)

### 後端資料入口點

當從管理員建立客戶或訂單時，商戶可以輸入客戶資訊、地址資料和付款資料。

![後端資料入口點](../../assets/security-compliance/backend-data-entry-points.svg)

### 後端資料存取點

Adobe Commerce和Magento Open Source在商家查看多種類型的網格時載入客戶資訊，按一下網格以查看詳細資訊，並執行各種其他任務。

![後端資料存取點](../../assets/security-compliance/backend-data-access-points.svg)

## 資料庫實體

Adobe Commerce和Magento Open Source主要在客戶、地址、訂單、報價和付款表中儲存特定於客戶的資訊。 其他表包含對客戶ID的引用。

### 客戶資料

Adobe Commerce和Magento Open Source可配置為儲存以下客戶屬性：

- 出生日期
- 電子郵件
- 名字
- 性別
- 姓氏
- 中間名稱/初始
- 名稱前置詞
- 名稱尾碼

>[!NOTE]
>
>根據當前的安全和隱私最佳做法，在收集或處理此類資料之前，請確保您知道與儲存客戶的完整出生日（月、日、年）以及其他個人標識符（如全名）相關的任何潛在法律和安全風險。

#### `customer_entity` 和「customer_entity」引用

中的以下列 `customer_entity` 表包含客戶資訊：

| 列 | 資料類型 |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | 日期 |
| `gender` | smallint(5) |

這些表引用 `customer_entity` 並且可以包含自定義客戶屬性：

| 表格 | 列 | 資料類型 |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | 日期 |
| `customer_entity_decimal` | `value` | 十進位(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文本 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` 表

中的以下列 `customer_grid_flat` 表包含客戶資訊：

| 列 | 資料類型 |
| -------------------- | ------------ |
| `name` | 文本 |
| `email` | varchar(255) |
| `dob` | 日期 |
| `gender` | int(11) |
| `shipping_full` | 文本 |
| `billing_full` | 文本 |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### 地址資料

Adobe Commerce和Magento Open Source儲存以下客戶屬性：

- 城市
- 公司
- 國家/地區
- 傳真
- 名字
- 姓氏
- 中間名稱/初始
- 名稱前置詞
- 名稱尾碼
- 電話號碼
- 省/自治區
- 省/自治區ID
- 街道地址
- 增值稅編號
- 郵遞區號

#### `customer_address_entity` 和 `customer_address_entity` 參照

中的以下列 `customer_address_entity` 表包含客戶資訊：

| 列 | 資料類型 |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | 文本 |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

這些表引用 `customer_address_entity` 並且可以包含自定義客戶屬性：

| 表格 | 列 | 資料類型 |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | 日期 |
| `customer_address_entity_decimal` | `value` | 十進位(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文本 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 訂單資料

的 `sales_order` 相關表包含客戶名稱、開單地址和發運地址以及相關資料。

#### `sales_order` 表

中的以下列 `sales_order` 表包含客戶資訊：

| 列 | 資料類型 |
| --------------------- | ------------ |
| `customer_dob` | 日期 |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` 表

的 `sales_order_address` 表包含客戶地址。

| 列 | 資料類型 |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` 表

中的以下列 `sales_order_grid` 表包含客戶資訊：

| 列 | 資料類型 |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### 報價資料

報價包含客戶的姓名、電子郵件、地址和相關資訊。

#### `quote` 表

中的以下列 `quote` 表包含客戶資訊：

| 列 | 資料類型 |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | 日期 |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` 表

中的以下列 `quote_address` 表包含客戶資訊：

| 列 | 資料類型 |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### 付款資料

的 `sales_order_payment` 表包括信用卡資訊和其他交易資訊。

| 列 | 資料類型 |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | 文本 |

### 邀請資料

Adobe Commerce和Magento Open Source可以配置，以便客戶可以向私人銷售和活動發送邀請。

#### `magento_invitation` 表

的 `magento_invitation` 表包含客戶ID、電子郵件和推薦ID。

| 列 | 資料類型 |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` 表

的 `magento_invitation_track` 表還包含客戶資訊。

| 列 | 資料類型 |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### 引用客戶的雜項表

下表包含 `customer_id` 列：

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
