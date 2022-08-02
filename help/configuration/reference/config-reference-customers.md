---
title: 客戶配置路徑參考
description: 請參閱客戶配置值清單。
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 2%

---


# 客戶配置路徑參考

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **客戶**。

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，它應該在原始碼管理中。 要可選地覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數覆蓋配置設定](override-config-settings.md#environment-variables)。 此主題確實 _不_ 清單 [敏感值和系統特定值](config-reference-sens.md)。

## 新聞稿路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **新聞稿**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 允許來賓訂閱 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要確認 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認電子郵件發件人 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認電子郵件模板 | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功電子郵件發件人 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功電子郵件模板 | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取消訂閱電子郵件發件人 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取消訂閱電子郵件模板 | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 客戶配置路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **客戶配置**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 聯機分鐘間隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共用客戶帳戶 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用自動分配至客戶組 | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基於 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設組 | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效增值稅ID的組 — 國內 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效增值稅ID的組 — 聯合內 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無效增值稅ID的組 | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證錯誤組 | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 對每個事務進行驗證 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基於增值稅標識禁用自動組更改的預設值 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上顯示增值稅編號 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設歡迎電子郵件 | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設歡迎電子郵件，無密碼 | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 要求確認電子郵件 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認連結電子郵件 | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歡迎電子郵件 | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成人性化的客戶ID | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重置保護類型 | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大密碼重置請求數 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重置請求之間的最小時間 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 忘記電子郵件模板 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提醒電子郵件模板 | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重置密碼模板 | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼模板電子郵件發件人 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 恢復連結到期期（小時） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在登錄/忘記密碼表單上啟用自動完成 | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 所需字元類數 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定帳戶的最大登錄失敗數 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小密碼長度 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定時間（分鐘） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 街道地址中的行數 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示前置詞 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 前置詞下拉選項 | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示中間名稱（初始） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示尾碼 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 尾碼下拉選項 | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示出生日期 | `customer/address/dob_show`<br>根據當前的安全和隱私最佳做法，在收集或處理此類資料之前，請確保您知道與儲存客戶的完整出生日（月、日、年）以及其他個人標識符（如全名）相關的任何潛在法律和安全風險。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示稅/增值稅編號 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示性別 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用儲存信用功能 | `customer/magento_customerbalance/is_enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 向客戶顯示商店信用歷史記錄 | `customer/magento_customerbalance/show_history` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 自動退款商店貸項 | `customer/magento_customerbalance/refund_automatically` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 儲存信用更新電子郵件發件人 | `customer/magento_customerbalance/email_identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 儲存信用更新電子郵件模板 | `customer/magento_customerbalance/email_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 登錄後將客戶重定向到帳戶儀表板 | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文本 | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文本一行 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用客戶細分功能 | `customer/magento_customersegment/is_enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在店面啟用驗證碼 | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 字型 | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示模式 | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 嘗試登錄失敗的次數 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼超時（分鐘） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 符號數 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼中使用的符號 | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 區分大小寫 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

## 希望清單路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **願望清單**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 已啟用 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用多個願望清單 | `wishlist/general/multiple_enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 多個願望清單數 | `wishlist/general/multiple_wishlist_number` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 電子郵件發件人 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件模板 | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許發送的最大電子郵件數 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件文本長度限制 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示願望清單摘要 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

## 邀請路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **邀請**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用邀請功能 | `magento_invitation/general/enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 啟用店面邀請 | `magento_invitation/general/enabled_on_front` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 引用客戶組 | `magento_invitation/general/registration_use_inviter_group` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 新帳戶註冊 | `magento_invitation/general/registration_required_invitation` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許客戶將自定義消息添加到邀請電子郵件 | `magento_invitation/general/allow_customer_message` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 允許一次發送的最大邀請數 | `magento_invitation/general/max_invitation_amount_per_send` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 客戶邀請電子郵件發件人 | `magento_invitation/email/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 客戶邀請電子郵件模板 | `magento_invitation/email/template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 獎勵積分路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **獎勵積分**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用獎勵積分功能 | `magento_reward/general/is_enabled` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 在店面啟用獎勵積分功能 | `magento_reward/general/is_enabled_on_front` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 客戶可能會看到獎勵積分歷史記錄 | `magento_reward/general/publish_history` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 獎勵積分餘額贖回閾值 | `magento_reward/general/min_points_balance` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 上限獎勵積分餘額 | `magento_reward/general/max_points_balance` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 獎勵積分在（天）後到期 | `magento_reward/general/expiration_days` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 獎勵積分到期計算 | `magento_reward/general/expiry_calculation` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 自動退款獎勵積分 | `magento_reward/general/refund_automatically` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 自動從退款金額中扣除獎勵積分 | `magento_reward/general/deduct_automatically` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 登錄頁 | `magento_reward/general/landing_page` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 購買 | `magento_reward/points/order` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 註冊 | `magento_reward/points/register` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 新聞稿註冊 | `magento_reward/points/newsletter` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 將邀請轉換為客戶 | `magento_reward/points/invitation_customer` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 邀請客戶轉換數量限制 | `magento_reward/points/invitation_customer_limit` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 將邀請轉換為訂單 | `magento_reward/points/invitation_order` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 邀請至訂單轉換數量限制 | `magento_reward/points/invitation_order_limit` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 邀請轉換為訂單獎勵 | `magento_reward/points/invitation_order_frequency` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 審閱提交 | `magento_reward/points/review` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 已獎勵的審閱提交數量限制 | `magento_reward/points/review_limit` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 電子郵件發件人 | `magento_reward/notification/email_sender` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 預設訂閱客戶 | `magento_reward/notification/subscribe_by_default` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 餘額更新電子郵件 | `magento_reward/notification/balance_update_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 獎勵積分到期警告電子郵件 | `magento_reward/notification/expiry_warning_template` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 過期警告（天）之前 | `magento_reward/notification/expiry_day_before` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 促銷路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **促銷**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用提醒電子郵件 | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時分 | `promo/magento_reminder/minutes` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 開始時間 | `promo/magento_reminder/time` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 每次運行的最大電子郵件數 | `promo/magento_reminder/limit` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 電子郵件發送失敗閾值 | `promo/magento_reminder/threshold` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 提醒電子郵件發件人 | `promo/magento_reminder/identity` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 代碼長度 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼格式 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼前置詞 | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代碼尾碼 | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每X個字元划線 | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

## 禮品註冊路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **禮品註冊表**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用禮品註冊 | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大註冊者數 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件模板 | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件模板 | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大已發送電子郵件閾值 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件模板 | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

## 持久購物車路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **持久購物車**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用持久性 | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持久性生存期（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用「記住我」 | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「記住我」預設值 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 註銷時清除持久性 | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持久購物車 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持久願望清單 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留最近訂購的項 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留當前比較的產品 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持續比較歷史記錄 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 堅持最近查看的產品 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留客戶組成員資格和細分 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;
