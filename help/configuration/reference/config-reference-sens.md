---
title: 敏感和系統特定路徑
description: 請參閱系統特定和敏感配置值的清單。
source-git-commit: 019d638403f2dc3e170a56842335da203126d8a6
workflow-type: tm+mt
source-wordcount: '3711'
ht-degree: 2%

---


# 敏感和系統特定設定

本主題列出了特定於系統和敏感設定的配置路徑：

- 的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將系統特定的設定寫入系統特定的配置檔案， `app/etc/env.php`，應 _不_ 在原始碼管理中。 它還將所有Commerce實例的共用配置寫入 `app/etc/config.php`，此檔案 _應該_ 在原始碼管理中。
- 的 [`magento config:sensitive:set` 命令](../cli/set-configuration-values.md) 將敏感設定寫入 `app/etc/env.php`。

   也可以使用配置變數設定敏感值，如中所述 [使用環境變數覆蓋配置設定](../reference/override-config-settings.md#environment-variables)。

有關其他配置路徑的清單，請參閱：

- [除付款外的所有配置路徑](../reference/config-reference-general.md)
- [付款配置路徑](../reference/config-reference-payment.md)。

>[!INFO]
>
>本主題中列出的所有配置路徑都是敏感的。 的 `System-specific?` 列顯示哪些值也特定於系統。

## 一般類別敏感和系統特定路徑

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **常規**。

### Web路徑敏感和系統特定的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **Web**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基本URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 基本連結URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 靜態視圖檔案的基URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 用戶媒體檔案的基URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 安全基URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 安全基本連結URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 靜態視圖檔案的安全基URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 用戶媒體檔案的安全基URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 預設Web URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 預設無路由URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie路徑 | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie域 | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie生存期 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 僅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 貨幣設定敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **幣種設定**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 儲存對電子郵件地址敏感的系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **電子郵件配置** > **常規** > **儲存電子郵件地址**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 發件人名稱 | `trans_email/ident_general/name` |  |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人電子郵件 | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人名稱 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人電子郵件 | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人名稱 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人電子郵件 | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人名稱 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人電子郵件 | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人名稱 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發件人電子郵件 | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 聯繫人敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **聯繫人**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將電子郵件發送到 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件發件人 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件模板 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### New Relic報告敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **常規** > **新羅利克報告**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 新舊帳戶ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic應用程式ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic API密鑰 | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Insights API密鑰 | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新建Relic API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Insights API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 客戶類別敏感和特定於系統的路徑

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **客戶**。

### 客戶配置敏感和特定於系統的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **客戶配置**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 預設電子郵件域 | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 目錄類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **目錄**。

### 目錄敏感和系統特定的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **目錄** > **目錄**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| YouTubeAPI密鑰 | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器主機名 | `catalog/search/solr_server_hostname` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器埠 | `catalog/search/solr_server_port` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器用戶名 | `catalog/search/solr_server_username` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器密碼 | `catalog/search/solr_server_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器路徑 | `catalog/search/solr_server_path` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器主機名 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器埠 | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch索引前置詞 | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 啟用ElasticsearchHTTP身份驗證 | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP用戶名 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP密碼 | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Elasticsearch伺服器超時 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 清單敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **目錄** > **庫存**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| GoogleAPI密鑰 | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### XML站點地圖敏感路徑和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **目錄** > **XML站點地圖**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 銷售類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **銷售**。

### 發運設定敏感和系統特定的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **裝運設定**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 國家/地區 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 區域/州 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址行2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時帳戶 | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 銷售電子郵件敏感和特定於系統的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **銷售電子郵件**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將訂單電子郵件副本發送到 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將訂單注釋電子郵件副本發送到 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發票電子郵件副本發送到 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發票注釋電子郵件副本發送到 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發運電子郵件副本發送到 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發運注釋電子郵件副本發送到 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將貸項通知單電子郵件副本發送到 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將貸項通知單注釋電子郵件副本發送到 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將「裝貨就緒」電子郵件副本發送到 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 簽出敏感路徑和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **簽出**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將付款失敗的電子郵件副本發送到 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### GoogleAPI敏感路徑和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **GoogleAPI**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器ID | `google/analytics/container_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 傳遞方法敏感和系統特定的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **傳遞方法**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 網關URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安全網關URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 標題 | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 用戶ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 用戶ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問許可證號 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 跟蹤XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發貨人編號 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 調試 | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 帳戶ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 鍵 | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 儀表號 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 調試 | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 帳號 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 銷售敏感型和特定於系統的路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **銷售**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 聯繫人姓名 | `sales/magento_rma/store_name` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `sales/magento_rma/city` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 省/自治區 | `sales/magento_rma/region_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `sales/magento_rma/zip` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 國家/地區 | `sales/magento_rma/country_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA電子郵件副本發送到 | `sales_email/magento_rma/copy_to` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA授權電子郵件副本發送到 | `sales_email/magento_rma_auth/copy_to` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA注釋電子郵件副本發送到 | `sales_email/magento_rma_comment/copy_to` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA注釋電子郵件副本發送到 | `sales_email/magento_rma_customer_comment/copy_to` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### GoogleAPI路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **GoogleAPI**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帳號 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 高級類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **高級**。

### 管理員敏感路徑和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **管理**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自定義管理URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定義管理路徑 | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 系統敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **系統**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問清單 | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件發件人錯誤 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 開發人員敏感和系統特定路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **開發人員**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允許的IP（逗號分隔） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 高級類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **高級**。

### 系統路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **系統**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主機 | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 埠(25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端主機 | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端埠 | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 開發人員路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **高級** > **開發人員**。

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將JS錯誤記錄到會話儲存密鑰 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;&quot;

## 付款敏感和系統特定路徑

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **銷售** > **付款**。

### 常規變數

| 名稱 | 配置路徑 | 只做商業？ | 加密？ |
|--------------|--------------|--------------|--------------|
| 商人國家 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

>[!INFO]
>
>您對此變數的選擇決定了 [國際路徑](#international-paths) 你可以用。

### PayPal敏感和系統特定路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 與PayPal商家帳戶關聯的電子郵件（可選） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶帳戶ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發佈者ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 登錄 | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定義終結點主機名或IP地址 | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 調試模式 | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 調試模式 | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑據 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### PayPal Payflow Pro敏感和系統特定路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用戶 | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定義路徑 | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 用戶 | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 合作夥伴 | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主機 | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 調試模式 | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑據 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 信用卡設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### PayPal Payflow連結敏感和系統特定路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用戶 | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 使用代理 | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理主機 | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理埠 | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 調試模式 | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 取消URL和返回URL的URL方法 | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 調試模式 | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑據 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### PayPal Payments Pro敏感和系統特定路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API用戶名 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密碼 | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API簽名 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API證書 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主機 | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑據 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### PayPal Payments Pro托管敏感和特定於系統的路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 調試模式 | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑據 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### Braintree敏感和系統特定路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商戶ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 公鑰 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 私鑰 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶帳戶ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 卡恩特商戶ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 覆蓋商戶名稱 | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電話 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 支票/貨幣訂單路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將支票發送到 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;

### 國際路徑

| 名稱 | 配置路徑 | 只做商業？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 事務密鑰 | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_au/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_au/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_au/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_au/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_au/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_au/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `payment_au/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_au/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_au/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_au/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_au/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_au/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_au/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_es/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_es/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_es/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_es/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_es/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_es/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_es/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 調試 | `payment_es/worldpay/debug` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_es/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_es/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_es/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_es/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_es/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_es/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_es/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_nz/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_nz/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_nz/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_nz/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_nz/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_nz/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_nz/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_nz/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_nz/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理主機 | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 調試模式 | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 取消URL和返回URL的URL方法 | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_us/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_us/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_us/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_us/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_us/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_us/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_us/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_us/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_us/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_us/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_us/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_gb/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_gb/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_gb/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_gb/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_gb/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_gb/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_gb/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_gb/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_gb/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_de/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_de/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_de/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_de/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 事務密鑰 | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_de/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_de/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 調試 | `payment_de/worldpay/debug` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_de/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_de/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_de/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_de/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_de/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_de/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_de/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 事務密鑰 | `payment_other/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_other/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_other/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/cybersource/order_status` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_other/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_other/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_other/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_other/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_other/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_other/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_other/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_other/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_other/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_other/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_other/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_ca/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_ca/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_ca/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/cybersource/order_status` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| Test模式 | `payment_ca/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_ca/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 遠程管理員授權密碼 | `payment_ca/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_ca/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_ca/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_ca/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_ca/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_ca/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_ca/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_ca/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_ca/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_hk/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_hk/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_hk/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_hk/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_hk/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_hk/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_hk/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密鑰 | `payment_hk/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_hk/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_hk/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_hk/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_hk/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_hk/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_jp/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_jp/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_jp/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_jp/cybersource/order_status` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Test模式 | `payment_jp/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_jp/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_jp/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_jp/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_jp/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_jp/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_jp/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_jp/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_jp/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_jp/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_jp/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_fr/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_fr/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_fr/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_fr/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_fr/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_fr/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_fr/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_fr/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_fr/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_fr/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_fr/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_fr/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_fr/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_fr/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務詳細資訊URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_it/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_it/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_it/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_it/cybersource/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_it/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_it/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Test模式 | `payment_it/worldpay/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_it/eway/sandbox_flag` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API密鑰 | `payment_it/eway/live_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Live API密碼 | `payment_it/eway/live_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_it/eway/live_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密鑰 | `payment_it/eway/sandbox_api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密碼 | `payment_it/eway/sandbox_api_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客戶端加密密鑰 | `payment_it/eway/sandbox_encryption_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密鑰 | `fraud_protection/signifyd/api_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_au/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_au/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_es/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_es/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_es/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 |
| SFTP憑據 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_nz/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_nz/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_nz/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_nz/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_nz/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_nz/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_nz/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_nz/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_nz/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_nz/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_us/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_us/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_us/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_us/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_us/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_us/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_us/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_us/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_gb/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_gb/cybersource/transaction_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_gb/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_gb/cybersource/access_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_gb/cybersource/secret_key` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 事務密鑰 | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_gb/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_gb/worldpay/response_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_gb/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_gb/worldpay/auth_password` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_de/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_de/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_de/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 遠程管理員安裝ID | `payment_de/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_de/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_other/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_other/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_other/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_other/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_other/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_ca/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_ca/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_ca/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_ca/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_ca/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_hk/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_hk/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_hk/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_hk/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_hk/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_hk/worldpay/signature_fields` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_jp/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_jp/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_jp/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |
| 遠程管理員安裝ID | `payment_jp/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_jp/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_jp/worldpay/signature_fields` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_fr/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_fr/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_fr/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_fr/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_fr/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_fr/worldpay/signature_fields` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑據 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票付款 | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登錄ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment_it/cybersource/merchant_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置檔案ID | `payment_it/cybersource/profile_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_it/worldpay/installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_it/worldpay/admin_installation_id` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| MD5事務機密 | `payment_it/worldpay/md5_secret` | ![僅限商業](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;&quot;
