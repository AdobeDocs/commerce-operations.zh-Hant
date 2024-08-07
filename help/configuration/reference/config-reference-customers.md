---
title: 客戶設定路徑參考
description: 檢視客戶設定值清單。
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# 客戶設定路徑參考

本節列出&#x200B;**商店** >設定> **設定** > **客戶**&#x200B;底下「管理員」中選項的變數名稱和設定路徑。

[`magento app:config:dump`命令](../cli/export-configuration.md)將這些值寫入到共用組態檔`app/etc/config.php`，它應該是在原始檔控制中。 若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱[使用環境變數覆寫組態設定](override-config-settings.md#environment-variables)。 此主題&#x200B;_不_&#x200B;列出[敏感值和系統特定值](config-reference-sens.md)。

## Newsletter路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **電子報**&#x200B;的Admin中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 允許訪客訂閱 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要確認 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認電子郵件寄件者 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認電子郵件範本 | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功電子郵件寄件者 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功電子郵件範本 | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取消訂閱電子郵件寄件者 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取消訂閱電子郵件範本 | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 客戶設定路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **客戶** > **客戶組態**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 線上分鐘間隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共用客戶帳戶 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用自動指定至客戶群組 | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 稅捐計算依據 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設群組 | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效VAT ID的群組 — 國內 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效VAT ID的群組 — 內部聯集 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| VAT ID無效的群組 | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證錯誤群組 | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證每個交易 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 根據VAT ID停用自動群組變更的預設值 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面顯示VAT編號 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設歡迎電子郵件 | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設的歡迎電子郵件（不含密碼） | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件寄件者 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要電子郵件確認 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認連結電子郵件 | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歡迎電子郵件 | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產生人性化的客戶ID | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設保護型別 | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設要求的最大數量 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設要求之間的最短時間 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 忘記電子郵件範本 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提醒電子郵件範本 | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重設密碼範本 | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼範本電子郵件寄件者 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 復原連結到期日（小時） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在登入/忘記密碼表單上啟用自動完成 | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 必要的字元類別數目 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定帳戶的最大登入失敗次數 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼長度下限 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定時間（分鐘） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 街道地址中的行數 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示前置詞 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 首碼下拉式清單選項 | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示中間名（初始） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示尾碼 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 尾碼下拉式清單選項 | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示出生日期 | `customer/address/dob_show`<br>根據目前的安全與隱私權最佳實務，在收集或處理這類資料之前，請務必瞭解任何與儲存客戶完整出生日期（月、日、年）相關的潛在法律與安全性風險，以及其他個人識別碼，例如全名。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示稅捐/VAT編號 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示性別 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用商店信用功能 | `customer/magento_customerbalance/is_enabled` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 向客戶顯示商店信用記錄 | `customer/magento_customerbalance/show_history` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 自動退款商店點數 | `customer/magento_customerbalance/refund_automatically` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 儲存信用更新電子郵件寄件者 | `customer/magento_customerbalance/email_identity` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 商店信用更新電子郵件範本 | `customer/magento_customerbalance/email_template` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 登入後將客戶重新導向至帳戶控制面板 | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文字 | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文字一行 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用客戶區段功能 | `customer/magento_customersegment/is_enabled` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 在店面啟用驗證碼 | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 字型 | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示模式 | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 登入嘗試失敗的次數 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼逾時（分鐘） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 符號數 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼中使用的符號 | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 區分大小寫 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 希望清單路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **願望清單**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 已啟用 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用多個希望清單 | `wishlist/general/multiple_enabled` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 多個希望清單的數量 | `wishlist/general/multiple_wishlist_number` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 電子郵件寄件者 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件範本 | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許傳送的最大電子郵件數 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件文字長度限制 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示希望清單摘要 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 邀請路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **邀請**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用邀請功能 | `magento_invitation/general/enabled` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 啟用店面的邀請 | `magento_invitation/general/enabled_on_front` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 引用的客戶群組 | `magento_invitation/general/registration_use_inviter_group` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新帳戶註冊 | `magento_invitation/general/registration_required_invitation` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允許客戶新增自訂訊息至邀請電子郵件 | `magento_invitation/general/allow_customer_message` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允許一次傳送的最大邀請數 | `magento_invitation/general/max_invitation_amount_per_send` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 客戶邀請電子郵件寄件者 | `magento_invitation/email/identity` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 客戶邀請電子郵件範本 | `magento_invitation/email/template` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 獎勵點數路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **獎勵點數**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用獎勵點數功能 | `magento_reward/general/is_enabled` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 啟用店面的獎勵點數功能 | `magento_reward/general/is_enabled_on_front` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 客戶可檢視獎勵點數歷史記錄 | `magento_reward/general/publish_history` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 獎勵點數餘額兌換臨界值 | `magento_reward/general/min_points_balance` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 將獎勵點數餘額限制在 | `magento_reward/general/max_points_balance` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 獎勵點數的有效期限（天） | `magento_reward/general/expiration_days` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 獎勵積分到期計算 | `magento_reward/general/expiry_calculation` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 自動退款獎勵積分 | `magento_reward/general/refund_automatically` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 自動從退款金額中扣除獎勵積分 | `magento_reward/general/deduct_automatically` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 登陸頁面 | `magento_reward/general/landing_page` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 購買 | `magento_reward/points/order` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 註冊 | `magento_reward/points/register` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| Newsletter註冊 | `magento_reward/points/newsletter` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 將邀請轉換為客戶 | `magento_reward/points/invitation_customer` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 邀請客戶轉換數量限制 | `magento_reward/points/invitation_customer_limit` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 將邀請轉換為訂單 | `magento_reward/points/invitation_order` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 訂單轉換邀請數量限制 | `magento_reward/points/invitation_order_limit` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 邀請轉換至訂單獎勵 | `magento_reward/points/invitation_order_frequency` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 檢閱提交 | `magento_reward/points/review` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 獎勵複查提交數量限制 | `magento_reward/points/review_limit` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 電子郵件寄件者 | `magento_reward/notification/email_sender` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 預設訂閱客戶 | `magento_reward/notification/subscribe_by_default` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 餘額更新電子郵件 | `magento_reward/notification/balance_update_template` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 獎勵點數到期警告電子郵件 | `magento_reward/notification/expiry_warning_template` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| （天）前到期警告 | `magento_reward/notification/expiry_day_before` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 促銷活動路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **促銷活動**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用提醒電子郵件 | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 一小時中的分鐘 | `promo/magento_reminder/minutes` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 開始時間 | `promo/magento_reminder/time` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 每次執行的最大電子郵件數 | `promo/magento_reminder/limit` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 電子郵件傳送失敗閾值 | `promo/magento_reminder/threshold` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 提醒電子郵件寄件者 | `promo/magento_reminder/identity` | ![僅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 程式碼長度 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼格式 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼首碼 | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼尾碼 | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將每X個字元加上破折號 | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 贈品登入路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **禮品登入**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用贈品登入 | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最多註冊者 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件範本 | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件寄件者 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件範本 | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件寄件者 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大已傳送電子郵件臨界值 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件範本 | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件寄件者 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 永續性購物車路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **客戶** > **永久購物車**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用持續性 | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持續性存留期（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用「記住我」 | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「記住我」預設值 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 登出時清除持續性 | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留購物車 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留希望清單 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留最近訂購的專案 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留目前比較的產品 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留比較歷史記錄 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留最近檢視的產品 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留客戶群組成員資格和細分 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
