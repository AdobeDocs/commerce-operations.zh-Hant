---
title: 敏感和系統特定路徑
description: 請參閱系統特定和敏感配置值的清單。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---


# 敏感和系統特定設定

本主題列出系統特定和敏感設定的配置路徑：

- 此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將系統特定設定寫入系統特定配置檔案， `app/etc/env.php`, _not_ 在原始碼控制中。 它也會將所有Commerce例項的共用設定寫入 `app/etc/config.php`，此檔案 _show_ 在原始碼控制中。
- 此 [`magento config:sensitive:set` 命令](../cli/set-configuration-values.md) 將敏感設定寫入 `app/etc/env.php`.

   您也可以使用設定變數來設定敏感值，如 [使用環境變數來覆寫組態設定](../reference/override-config-settings.md#environment-variables).

如需其他設定路徑的清單，請參閱：

- [除付款外的所有配置路徑](../reference/config-reference-general.md)
- [付款配置路徑](../reference/config-reference-payment.md).

>[!INFO]
>
>此主題中列出的所有配置路徑都是敏感路徑。 此 `System-specific?` 欄顯示哪些值也是系統特定值。

## 一般類別敏感和系統特定路徑

本節列出「管理員」下方的選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **一般**.

### Web路徑敏感且系統專屬路徑

這些設定值可在 **商店** >設定> **設定** > **一般** > **Web**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基本URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 基本連結URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 靜態檢視檔案的基礎URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 用戶媒體檔案的基本URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 安全基URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 安全基礎連結URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 靜態檢視檔案的安全基底URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 用戶媒體檔案的安全基URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 預設Web URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 預設無路由URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie路徑 | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie網域 | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie期限 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 僅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 貨幣設定敏感且系統特定的路徑

這些設定值可在 **商店** >設定> **設定** > **一般** > **貨幣設定**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 儲存敏感電子郵件地址和系統特定路徑

這些設定值可在 **商店** >設定> **電子郵件設定** > **一般** > **儲存電子郵件地址**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 寄件者名稱 | `trans_email/ident_general/name` |  |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 聯繫人敏感和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **一般** > **聯繫人**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 傳送電子郵件至 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件寄件者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件範本 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic報告敏感和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **一般** > **New Relic報表**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic帳戶ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic應用程式ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic API密鑰 | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Insights API密鑰 | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 前瞻分析API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 客戶類別敏感且系統專屬的路徑

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **客戶**.

### 對客戶配置敏感且特定於系統的路徑

這些設定值可在 **商店** >設定> **設定** > **客戶** > **客戶設定**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 預設電子郵件網域 | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 目錄類別

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **目錄**.

### 目錄敏感和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **目錄**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| YouTube API密鑰 | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器主機名 | `catalog/search/solr_server_hostname` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器埠 | `catalog/search/solr_server_port` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器用戶名 | `catalog/search/solr_server_username` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器密碼 | `catalog/search/solr_server_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器路徑 | `catalog/search/solr_server_path` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器主機名 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器埠 | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch索引前置詞 | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 啟用ElasticsearchHTTP驗證 | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP使用者名稱 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP密碼 | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP使用者名稱 | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| ElasticsearchHTTP密碼 | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch伺服器主機名 | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| OpenSearch伺服器埠 | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| OpenSearch索引前置詞 | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 啟用OpenSearch HTTP驗證 | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP使用者名稱 | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP密碼 | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch伺服器超時 | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>Adobe Commerce 2.4.6導入了OpenSearch設定。

### 清單敏感和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **庫存**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API金鑰 | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML Sitemap敏感和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **XML Sitemap**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 銷售類別

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **銷售**.

### 發運設定敏感且特定於系統的路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **運送設定**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 國家/地區 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 地區/國家 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址2號線 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時帳戶 | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 敏感和系統特定的銷售電子郵件路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **銷售電子郵件**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將訂單電子郵件副本發送到 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將訂單注釋電子郵件副本發送到 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發票電子郵件副本發送到 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發票注釋電子郵件副本發送到 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發運電子郵件副本發送到 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發運注釋電子郵件副本發送到 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將貸項通知單電子郵件副本發送至 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將貸項通知單備注電子郵件副本發送到 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將「裝貨就緒」電子郵件副本發送至 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 對結帳敏感且系統特定的路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **結帳**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將付款失敗的電子郵件副本發送到 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API敏感且系統專屬的路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **Google API**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器Id | `google/analytics/container_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 傳送方法敏感且系統專屬的路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **傳送方法**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 網關URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安全網關URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 標題 | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用者ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 使用者ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問許可證號 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 追蹤XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 托運人編號 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 除錯 | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 帳戶ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 金鑰 | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 儀表號 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 除錯 | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 帳號 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 銷售敏感型和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **銷售**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 聯繫人姓名 | `sales/magento_rma/store_name` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `sales/magento_rma/city` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 州/省 | `sales/magento_rma/region_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `sales/magento_rma/zip` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 國家/地區 | `sales/magento_rma/country_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA電子郵件副本發送到 | `sales_email/magento_rma/copy_to` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA授權電子郵件副本發送到 | `sales_email/magento_rma_auth/copy_to` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA注釋電子郵件副本發送到 | `sales_email/magento_rma_comment/copy_to` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將RMA注釋電子郵件副本發送到 | `sales_email/magento_rma_customer_comment/copy_to` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API路徑

這些設定值可在 **商店** >設定> **設定** > **銷售** > **Google API**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帳號 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 進階類別

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **進階**.

### 管理敏感和系統特定的路徑

這些設定值可在 **商店** >設定> **設定** > **進階** > **管理**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自訂管理URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自訂管理路徑 | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 系統敏感路徑和系統特定路徑

這些設定值可在 **商店** >設定> **設定** > **進階** > **系統**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件人 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問清單 | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 錯誤電子郵件寄件者 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開發人員敏感且系統專屬的路徑

這些設定值可在 **商店** >設定> **設定** > **進階** > **開發人員**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允許的IP（以逗號分隔） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 進階類別

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **進階**.

### 系統路徑

這些設定值可在 **商店** >設定> **設定** > **進階** > **系統**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主機 | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 埠(25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端主機 | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端埠 | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開發人員路徑

這些設定值可在 **商店** >設定> **設定** > **進階** > **開發人員**.

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將JS錯誤記錄到工作階段儲存金鑰 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 支付敏感型和系統特定路徑

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **銷售** > **付款**.

### 一般變數

| 名稱 | 設定路徑 | 只有商務？ | 加密？ |
|--------------|--------------|--------------|--------------|
| 商人國家 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>您對此變數的選擇決定 [國際道路](#international-paths) 您可以使用。

### PayPal敏感和系統特定路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 與PayPal商家帳戶相關聯的電子郵件（可選） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家帳戶ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發佈者ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 登入 | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定義終結點主機名或IP地址 | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 除錯模式 | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 除錯模式 | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑證 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro敏感且特定於系統的路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自訂路徑 | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 使用者 | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 合作夥伴 | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主機 | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 除錯模式 | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑證 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 信用卡設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 使用Proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理主機 | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理埠 | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 除錯模式 | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 取消URL和傳回URL的URL方法 | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 除錯模式 | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑證 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro敏感且特定於系統的路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API使用者名稱 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密碼 | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API簽章 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API憑證 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主機 | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑證 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro托管敏感且特定於系統的路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 除錯模式 | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| SFTP憑證 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintree敏感和系統特定路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商家ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 公開金鑰 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 私密金鑰 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家帳戶ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商戶ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 覆蓋商家名稱 | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電話 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 檢查/貨幣訂單路徑

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將支票發送到 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 國際道路

| 名稱 | 設定路徑 | 只有商務？ | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 交易金鑰 | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_au/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_au/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_au/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_au/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_au/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_au/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `payment_au/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_au/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_au/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_au/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_au/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_au/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_au/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_es/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_es/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_es/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_es/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_es/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_es/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_es/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 除錯 | `payment_es/worldpay/debug` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_es/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_es/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_es/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_es/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_es/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_es/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_es/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_nz/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_nz/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_nz/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_nz/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_nz/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_nz/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_nz/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_nz/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_nz/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 代理主機 | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理埠 | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 除錯模式 | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 取消URL和傳回URL的URL方法 | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_us/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_us/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_us/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_us/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_us/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_us/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_us/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_us/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_us/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_us/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_us/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_gb/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_gb/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_gb/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_gb/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_gb/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_gb/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_gb/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_gb/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_gb/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_de/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_de/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_de/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_de/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 交易金鑰 | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_de/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_de/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 除錯 | `payment_de/worldpay/debug` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_de/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_de/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_de/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_de/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_de/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_de/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_de/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 網關URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 交易金鑰 | `payment_other/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_other/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_other/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/cybersource/order_status` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_other/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_other/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_other/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_other/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_other/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_other/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_other/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_other/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_other/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_other/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_other/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_ca/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_ca/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_ca/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/cybersource/order_status` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 測試模式 | `payment_ca/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_ca/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 遠程管理員授權密碼 | `payment_ca/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_ca/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_ca/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_ca/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_ca/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_ca/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_ca/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_ca/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_ca/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_hk/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_hk/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_hk/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_hk/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_hk/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API金鑰 | `payment_hk/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_hk/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_hk/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_hk/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_hk/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_hk/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_jp/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_jp/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_jp/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_jp/cybersource/order_status` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_jp/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_jp/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_jp/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_jp/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_jp/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_jp/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_jp/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_jp/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_jp/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_jp/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_jp/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_fr/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_fr/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_fr/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_fr/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_fr/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_fr/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_fr/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_fr/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_fr/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_fr/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_fr/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_fr/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 網關URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資訊URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_it/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_it/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_it/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/cybersource/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 付款響應密碼 | `payment_it/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_it/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/worldpay/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_it/eway/sandbox_flag` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_it/eway/live_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_it/eway/live_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時客戶端加密密鑰 | `payment_it/eway/live_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_it/eway/sandbox_api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_it/eway/sandbox_api_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱用戶端加密金鑰 | `payment_it/eway/sandbox_encryption_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API金鑰 | `fraud_protection/signifyd/api_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  | ![系統特定](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_au/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_au/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_es/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_es/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_es/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 |
| SFTP憑證 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_nz/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_nz/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_nz/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_nz/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_nz/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_nz/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_nz/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_nz/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_nz/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_nz/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_us/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_us/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_us/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_us/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_us/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_us/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_us/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_us/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_gb/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_gb/cybersource/transaction_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_gb/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 訪問密鑰 | `payment_gb/cybersource/access_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密鑰 | `payment_gb/cybersource/secret_key` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_gb/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款響應密碼 | `payment_gb/worldpay/response_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_gb/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員授權密碼 | `payment_gb/worldpay/auth_password` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_de/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_de/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_de/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 遠程管理員安裝ID | `payment_de/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_de/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_other/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_other/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_other/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_other/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_other/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_ca/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_ca/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_ca/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_ca/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_ca/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_hk/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_hk/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_hk/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_hk/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_hk/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_hk/worldpay/signature_fields` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_jp/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_jp/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_jp/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 遠程管理員安裝ID | `payment_jp/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_jp/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_jp/worldpay/signature_fields` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_fr/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_fr/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_fr/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_fr/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_fr/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽名欄位 | `payment_fr/worldpay/signature_fields` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP憑證 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票 | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票發送到 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件客戶 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家的電子郵件 | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_it/cybersource/merchant_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_it/cybersource/profile_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_it/worldpay/installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠程管理員安裝ID | `payment_it/worldpay/admin_installation_id` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_it/worldpay/md5_secret` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
