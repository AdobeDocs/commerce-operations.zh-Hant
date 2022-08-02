---
title: 常規配置路徑引用
description: 請參見常規和高級配置值的清單。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 3%

---


# 常規和高級配置路徑參考

本主題列出了常規和高級配置路徑， _不_ [敏感值和系統特定值](config-reference-sens.md)。 的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，它應該在原始碼管理中。

要可選地覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數覆蓋配置設定](override-config-settings.md#environment-variables)。

## 一般類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **常規**。

### 常規路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** >常規> **常規**。

| 名稱 | 配置路徑 | 只做商業？ | 敏感？ |
|--------------|--------------|--------------|--------------|
| 預設國家/地區 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 允許國家/地區 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號為可選 | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 歐盟國家 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 頂級目標 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要狀態 | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果國家/地區為可選狀態，則允許選擇狀態 | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 時區 | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 區域設定 | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 重量單位 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 星期一 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 週末 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 訪問限制 | `general/restriction/is_active` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |
| 限制模式 | `general/restriction/mode` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |
| 啟動頁 | `general/restriction/http_redirect` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |
| 登錄頁 | `general/restriction/cms_page` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |
| HTTP響應 | `general/restriction/http_status` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |
| 儲存名稱 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 儲存電話號碼 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 儲存操作小時數 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 國家/地區 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 區域/州 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 郵遞區號 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 城市 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 街道地址 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 街道地址行2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 增值稅編號 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 啟用單儲存模式 | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style=&quot;table-layout:auto&quot;}

### Web路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **Web**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 將儲存代碼添加到URL | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動重定向到基本URL | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用Web伺服器重寫 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上使用安全URL | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在管理中使用安全URL | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用HTTP嚴格傳輸安全(HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 升級不安全的請求 | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 卸載器頭 | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS首頁 | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「CMS無路由」頁 | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「CMS無Cookie」頁 | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示CMS頁面的Breadcrumbs | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie生存期 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 僅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證REMOTE_ADDR。 | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上使用SID | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果禁用了Cookie，請重定向至「CMS」頁 | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果JavaScript被禁用，則顯示通知 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果禁用本地儲存，則顯示通知 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 貨幣設定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **幣種設定**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 基本貨幣 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設顯示貨幣 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的幣種 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 雅虎金融交易 | `TBD` |  |
| Fixer.io | `TBD` |  |
| WebServicex | `TBD` |  |
| 連接超時（秒） | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 連接超時（秒） | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 連接超時（秒） | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 服務 | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件收件人 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人錯誤 | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件模板 | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 聯繫人路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **聯繫人**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用聯繫我們 | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將電子郵件發送到 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件發件人 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件模板 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 報告路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **報告**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 年初至今開始 | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 當月開始 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 內容管理路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **內容管理**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用WYSIWYG編輯器 | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在WYSIWYG中為目錄使用媒體內容的靜態URL | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用層次結構功能 | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用層次結構元資料 | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 層次結構菜單的預設佈局 | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 新建Relic報告路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **新羅利克報告**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 啟用新舊檔案整合 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新建Relic應用程式名稱 | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

## 高級類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **高級**。

### 管理路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **管理**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 忘記密碼電子郵件模板 | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 忘記並重置電子郵件發件人 | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 用戶通知模板 | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟動頁 | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用自定義管理URL | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用自定義管理路徑 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理員帳戶共用 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重置保護類型 | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 恢復連結到期期（小時） | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大密碼重置請求數 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重置請求之間的最小時間 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將密鑰添加到URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 登錄區分大小寫 | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理會話生存時間（秒） | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定帳戶的最大登錄失敗數 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定時間（分鐘） | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼生存期（天） | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼更改 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用圖表 | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在管理員中啟用驗證碼 | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 字型 | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示模式 | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 嘗試登錄失敗的次數 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼超時（分鐘） | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 符號數 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼中使用的符號 | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 區分大小寫 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用的操作 | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 系統路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **系統**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 成功的消息生存期 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在以後重試正在進行的消息 | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗的消息生存期 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新消息生存期 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成計畫間隔 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提前計畫 | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 未在內運行時丟失 | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歷史清除間隔 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功歷史生命期 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗歷史記錄生存期 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用單獨的流程 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成計畫間隔 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提前計畫 | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 未在內運行時丟失 | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歷史清除間隔 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功歷史生命期 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗歷史記錄生存期 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成計畫間隔 | `system/cron/staging/schedule_generate_every` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 提前計畫 | `system/cron/staging/schedule_ahead_for` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 未在內運行時丟失 | `system/cron/staging/schedule_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 歷史清除間隔 | `system/cron/staging/history_cleanup_every` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 成功歷史生命期 | `system/cron/staging/history_success_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 失敗歷史記錄生存期 | `system/cron/staging/history_failure_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 使用單獨的流程 | `system/cron/staging/use_separate_process` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 生成計畫間隔 | `system/cron/catalog/event/schedule_generate_every` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 提前計畫 | `system/cron/catalog/event/schedule_ahead_for` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 未在內運行時丟失 | `system/cron/catalog/event/schedule_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 歷史清除間隔 | `system/cron/catalog/event/history_cleanup_every` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 成功歷史生命期 | `system/cron/catalog/event/history_success_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 失敗歷史記錄生存期 | `system/cron/catalog/event/history_failure_lifetime` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 使用單獨的流程 | `system/cron/catalog/event/use_separate_process` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 使用單獨的流程 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禁用電子郵件通信 | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定返迴路徑 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 返迴路徑電子郵件 | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已安裝的貨幣 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用HTTPS獲取源 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 更新頻率 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 上次更新 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用定時備份 | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 備份類型 | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 維護模式 | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日誌條目生存期，天 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日誌存檔頻率 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 快取應用程式 | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 公共內容的TTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬限期 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 導出配置 | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日誌中保存的天數 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 介質儲存 | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 選擇媒體資料庫 | `system/media_storage_configuration/media_database` (在Commerce 2.4.3中不建議使用) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 環境更新時間 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保存檔案，天 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用計畫檔案歷史記錄清除 | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件模板 | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;

### 開發人員路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **開發人員**。

| 名稱 | 配置路徑 | 只做商業？ |
|--------------|--------------|--------------|
| 工作流類型 | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許符號連結 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 微型HTML | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用Storefront的模板路徑提示 | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為管理員啟用模板路徑提示 | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將塊名稱添加到提示 | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 登錄到檔案 | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日誌到syslog | `dev/syslog/syslog_logging` |  |
| 為店面啟用 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為管理員啟用 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合併JavaScript檔案 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用JavaScript捆綁 | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 微型JavaScript檔案 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 翻譯策略 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將JS錯誤記錄到會話儲存 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合併CSS檔案 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 微型CSS檔案 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 映像適配器 | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 簽名靜態檔案 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同步索引 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 快取用戶定義的屬性 | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;&quot;
