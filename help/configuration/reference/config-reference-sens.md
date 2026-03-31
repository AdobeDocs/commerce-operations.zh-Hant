---
title: 敏感路徑和系統特定路徑
description: 瞭解Adobe Commerce的敏感和系統特定設定路徑。 探索安全的設定和環境變數管理。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# 敏感及系統專屬設定

本主題列出系統特定和敏感設定的組態路徑：

- [`magento app:config:dump`命令](../cli/export-configuration.md)會將系統特定的設定寫入系統特定的組態檔`app/etc/env.php`，該組態檔應該&#x200B;_不_&#x200B;在原始檔控制中。 它也會將所有Commerce執行個體的共用設定寫入`app/etc/config.php`，此檔案&#x200B;_應該_&#x200B;在原始檔控制中。
- [`magento config:sensitive:set`命令](../cli/set-configuration-values.md)會將敏感設定寫入`app/etc/env.php`。

  您也可以使用設定變數來設定敏感值，如[使用環境變數來覆寫設定設定](../reference/override-config-settings.md#environment-variables)中所述。

如需其他設定路徑的清單，請參閱：

- [除付款以外的所有設定路徑](../reference/config-reference-general.md)
- [付款設定路徑](../reference/config-reference-payment.md)。

>[!INFO]
>
>本主題中列出的所有設定路徑都是敏感的。 `System-specific?`欄顯示哪些值也是系統特定的。

## 一般類別敏感和系統特定路徑

本節列出&#x200B;**商店** >設定> **設定** > **一般**&#x200B;底下「管理員」中選項的變數名稱和設定路徑。

### 敏感的Web路徑和系統特定路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **一般** > **網頁**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基礎URL | `web/unsecure/base_url` |  | | 系統特定 | |
| 基礎連結URL | `web/unsecure/base_link_url` |  | | 系統特定 | |
| 靜態檢視檔案的基本URL | `web/unsecure/base_static_url` |  | | 系統特定 | |
| 使用者媒體檔案的基本URL | `web/unsecure/base_media_url` |  | | 系統特定 | |
| 安全基底URL | `web/secure/base_url` |  | | 系統特定 | |
| 安全基礎連結URL | `web/secure/base_link_url` |  | | 系統特定 | |
| 靜態檢視檔案的安全基底URL | `web/secure/base_static_url` |  | | 系統特定 | |
| 使用者媒體檔案的安全基底URL | `web/secure/base_media_url` |  | | 系統特定 | |
| 預設網頁URL | `web/default/front` |  | | 系統特定 | |
| 預設無路由URL | `web/default/no_route` |  | | 系統特定 | |
| Cookie路徑 | `web/cookie/cookie_path` |  | | 系統特定 | |
| Cookie網域 | `web/cookie/cookie_domain` |  | | 系統特定 | |
| Cookie期限 | `web/cookie/cookie_lifetime` |  | | 系統特定 | |
| 僅使用HTTP | `web/cookie/cookie_httponly` |  | | 系統特定 | |
| Cookie限制模式 | `web/cookie/cookie_restriction` |  | | 系統特定 | |

{style="table-layout:auto"}

### 貨幣設定敏感和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **一般** > **貨幣設定**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
| --- | --- | --- | --- | --- | --- |
| 錯誤電子郵件收件者 | `currency/import/error_email` |  | | | 敏感 |

{style="table-layout:auto"}

### 儲存區分電子郵件地址和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **電子郵件設定** > **一般** > **商店電子郵件地址**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 寄件者名稱 | `trans_email/ident_general/name` | | | | 敏感 |
| 寄件者電子郵件 | `trans_email/ident_general/email` |  | | | 敏感 |
| 寄件者名稱 | `trans_email/ident_sales/name` |  | | | 敏感 |
| 寄件者電子郵件 | `trans_email/ident_sales/email` |  | | | 敏感 |
| 寄件者名稱 | `trans_email/ident_support/name` |  | | | 敏感 |
| 寄件者電子郵件 | `trans_email/ident_support/email` |  | | | 敏感 |
| 寄件者名稱 | `trans_email/ident_custom1/name` |  | | | 敏感 |
| 寄件者電子郵件 | `trans_email/ident_custom1/email` |  | | | 敏感 |
| 寄件者名稱 | `trans_email/ident_custom2/name` |  | | | 敏感 |
| 寄件者電子郵件 | `trans_email/ident_custom2/email` |  | | | 敏感 |

{style="table-layout:auto"}

### 連絡人敏感路徑和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **一般** > **連絡人**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 傳送電子郵件至 | `contact/email/recipient_email` |  | | | 敏感 |
| 電子郵件寄件者 | `contact/email/sender_email_identity` |  | | | 敏感 |
| 電子郵件範本 | `contact/email/email_template` |  | | | 敏感 |

{style="table-layout:auto"}

### New Relic報告敏感和系統特定路徑

這些設定值可在&#x200B;**存放區** >設定> **設定** > **一般** > **New Relic報告**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic帳戶ID | `newrelicreporting/general/account_id` |  | | | 敏感 |
| New Relic應用程式Id | `newrelicreporting/general/app_id` |  | | | 敏感 |
| New Relic API金鑰 | `newrelicreporting/general/api` |  | 已加密 | | 敏感 |
| Insights API金鑰 | `newrelicreporting/general/insights_insert_key` |  | 已加密 | | 敏感 |
| NEW RELIC API URL | `newrelicreporting/general/api_url` |  | | 系統特定 | 敏感 |
| 前瞻分析API URL | `newrelicreporting/general/insights_api_url` |  | | 系統特定 | 敏感 |

{style="table-layout:auto"}

## 客戶類別敏感和系統特定路徑

本節列出&#x200B;**商店** >設定> **設定** > **客戶**&#x200B;底下「管理員」中選項的變數名稱和設定路徑。

### 客戶設定敏感和系統特定路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **客戶** > **客戶組態**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 預設電子郵件網域 | `customer/create_account/email_domain` |  | | 系統特定 | |

{style="table-layout:auto"}

## 目錄類別

此區段列出&#x200B;**商店** >設定> **設定** > **目錄**&#x200B;底下「管理員」中選項可用的變數名稱和設定路徑。

### 目錄敏感和系統特定路徑

這些設定值可在&#x200B;**存放區** >設定> **設定** > **目錄** > **目錄**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `catalog/productalert_cron/error_email` |  | | | 敏感 |
| YouTube API金鑰 | `catalog/product_video/youtube_api_key` |  | | | 敏感 |
| Solr伺服器主機名稱 | `catalog/search/solr_server_hostname` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| Solr伺服器連線埠 | `catalog/search/solr_server_port` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| Solr伺服器使用者名稱 | `catalog/search/solr_server_username` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| Solr伺服器密碼 | `catalog/search/solr_server_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| Solr伺服器路徑 | `catalog/search/solr_server_path` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| Elasticsearch伺服器主機名稱 | `catalog/search/elasticsearch_server_hostname` |  | | 系統特定 | 敏感 |
| Elasticsearch伺服器連線埠 | `catalog/search/elasticsearch_server_port` |  | | 系統特定 | 敏感 |
| Elasticsearch索引首碼 | `catalog/search/elasticsearch_index_prefix` |  | | 系統特定 | 敏感 |
| 啟用Elasticsearch HTTP驗證 | `catalog/search/elasticsearch_enable_auth` |  | | 系統特定 | |
| Elasticsearch HTTP使用者名稱 | `catalog/search/elasticsearch_username` |  | | 系統特定 | |
| Elasticsearch HTTP密碼 | `catalog/search/elasticsearch_password` |  | | 系統特定 | |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` |  | | 系統特定 | |
| Elasticsearch HTTP使用者名稱 | `catalog/search/elasticsearch_username` | | | 系統特定 | |
| Elasticsearch HTTP密碼 | `catalog/search/elasticsearch_password` | | | 系統特定 | |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` | | | 系統特定 | |
| OpenSearch伺服器主機名稱 | `catalog/search/opensearch_server_hostname` | | | 系統特定 | 敏感 |
| OpenSearch伺服器連線埠 | `catalog/search/opensearch_server_port` | | | 系統特定 | 敏感 |
| OpenSearch索引首碼 | `catalog/search/opensearch_index_prefix` | | | 系統特定 | 敏感 |
| 啟用OpenSearch HTTP驗證 | `catalog/search/opensearch_enable_auth` | | | 系統特定 | |
| OpenSearch HTTP使用者名稱 | `catalog/search/opensearch_username` | | | 系統特定 | |
| OpenSearch HTTP密碼 | `catalog/search/opensearch_password` | | | 系統特定 | |
| OpenSearch伺服器逾時 | `catalog/search/opensearch_server_timeout` | | | 系統特定 | |

{style="table-layout:auto"}

>[!NOTE]
>
>Adobe Commerce 2.4.6已匯入OpenSearch設定。

### 清查敏感路徑和系統特定路徑

這些組態值可在&#x200B;**存放區** >設定> **組態** > **目錄** > **詳細目錄**&#x200B;中的管理員中使用。

|名稱|設定路徑| Commerce版本支援|是否已加密？ |系統專用？ |敏感？ | |
--------------|--------------|--------------|--------------|--------------|--------------|
| Google API金鑰| `cataloginventory/source_selection_distance_based_google/api_key` ||加密| |敏感|

### XML Sitemap敏感路徑和系統特定路徑

這些組態值可在&#x200B;**存放區** >設定> **組態** > **目錄** > **XML Sitemap**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `sitemap/generate/error_email` |  | | | 敏感 |

{style="table-layout:auto"}

## 銷售類別

此區段列出&#x200B;**商店** >設定> **設定** > **銷售**&#x200B;底下「管理員」中選項可用的變數名稱和設定路徑。

### 運送設定敏感且系統特定的路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **銷售** > **送貨設定**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 國家 | `shipping/origin/country_id` |  | | | 敏感 |
| 地區/州 | `shipping/origin/region_id` |  | | | 敏感 |
| 郵遞區號 | `shipping/origin/postcode` |  | | | 敏感 |
| 城市 | `shipping/origin/city` |  | | | 敏感 |
| 街道地址 | `shipping/origin/street_line1` |  | | | 敏感 |
| 街道地址行2 | `shipping/origin/street_line2` |  | | | 敏感 |
| 即時帳戶 | `carriers/ups/is_account_live` |  | | 系統特定 | |

{style="table-layout:auto"}

### 銷售電子郵件敏感和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **銷售** > **銷售電子郵件**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將訂單電子郵件副本傳送至 | `sales_email/order/copy_to` |  | | | 敏感 |
| 將訂單評論電子郵件副本傳送至 | `sales_email/order_comment/copy_to` |  | | | 敏感 |
| 傳送發票電子郵件副本至 | `sales_email/invoice/copy_to` |  | | | 敏感 |
| 將發票註解電子郵件副本傳送至 | `sales_email/invoice_comment/copy_to` |  | | | 敏感 |
| 傳送出貨電子郵件副本至 | `sales_email/shipment/copy_to` |  | | | 敏感 |
| 將出貨評論電子郵件副本傳送至 | `sales_email/shipment_comment/copy_to` |  | | | 敏感 |
| 將銷退折讓單電子郵件副本傳送至 | `sales_email/creditmemo/copy_to` |  | | | 敏感 |
| 將銷退折讓單備註電子郵件副本傳送至 | `sales_email/creditmemo_comment/copy_to` |  | | | 敏感 |
| 將取車準備就緒電子郵件副本傳送至 | `sales_email/temando_pickup/copy_to` |  | | | 敏感 |

{style="table-layout:auto"}

### 簽出敏感和系統特定路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **銷售** > **結帳**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將付款失敗的電子郵件副本傳送到 | `checkout/payment_failed/copy_to` |  | | | 敏感 |

{style="table-layout:auto"}

### Google API敏感路徑和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **銷售** > **Google API**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器ID | `google/analytics/container_id` | 僅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}

### 敏感和系統特定路徑的傳送方法

這些設定值可在&#x200B;**商店** >設定> **設定** > **銷售** > **傳遞方法**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 閘道URL | `carriers/usps/gateway_url` |  | | | 敏感 |
| 安全閘道URL | `carriers/usps/gateway_secure_url` |  | | | 敏感 |
| 標題 | `carriers/usps/title` |  | | | |
| 使用者 ID | `carriers/usps/userid` |  | 已加密 | | 敏感 |
| 密碼 | `carriers/usps/password` |  | 已加密 | | 敏感 |
| 使用者 ID | `carriers/ups/username` |  | 已加密 | | 敏感 |
| 密碼 | `carriers/ups/password` |  | 已加密 | | 敏感 |
| 存取授權號碼 | `carriers/ups/access_license_number` |  | 已加密 | | 敏感 |
| 追蹤XML URL | `carriers/ups/tracking_xml_url` |  | | | 敏感 |
| 閘道XML URL | `carriers/ups/gateway_xml_url` |  | | | 敏感 |
| 託運人編號 | `carriers/ups/shipper_number` |  | | | 敏感 |
| 偵錯 | `carriers/ups/debug` |  | | | 敏感 |
| 帳戶 ID | `carriers/fedex/account` |  | 已加密 | | 敏感 |
| 索引鍵 | `carriers/fedex/key` |  | 已加密 | | 敏感 |
| 計量器編號 | `carriers/fedex/meter_number` |  | 已加密 | | 敏感 |
| 密碼 | `carriers/fedex/password` |  | 已加密 | | 敏感 |
| 存取識別碼 | `carriers/dhl/id` |  | 已加密 | | 敏感 |
| 密碼 | `carriers/dhl/password` |  | 已加密 | | 敏感 |
| 偵錯 | `carriers/dhl/debug` |  | | | |
| 帳號 | `carriers/dhl/account` |  | | | 敏感 |
| 閘道URL | `carriers/dhl/gateway_url` |  | | | 敏感 |
| 沙箱模式 | `carriers/fedex/sandbox_mode` |  | | | 敏感 |

{style="table-layout:auto"}

### 銷售敏感度與系統特定路徑

這些組態值可在&#x200B;**商店** >設定> **組態** > **銷售** > **銷售**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 連絡人姓名 | `sales/magento_rma/store_name` | 僅限Commerce Enterprise | | | 敏感 |
| 街道地址 | `sales/magento_rma/address` | 僅限Commerce Enterprise | | | 敏感 |
| 街道地址 | `sales/magento_rma/address1` |  | | | 敏感 |
| 城市 | `sales/magento_rma/city` | 僅限Commerce Enterprise | | | 敏感 |
| 州/省 | `sales/magento_rma/region_id` | 僅限Commerce Enterprise | | | 敏感 |
| 郵遞區號 | `sales/magento_rma/zip` | 僅限Commerce Enterprise | | | 敏感 |
| 國家 | `sales/magento_rma/country_id` | 僅限Commerce Enterprise | | | 敏感 |
| 傳送RMA電子郵件副本至 | `sales_email/magento_rma/copy_to` | 僅限Commerce Enterprise | | | 敏感 |
| 傳送RMA授權電子郵件副本至 | `sales_email/magento_rma_auth/copy_to` | 僅限Commerce Enterprise | | | 敏感 |
| 傳送RMA註解電子郵件副本至 | `sales_email/magento_rma_comment/copy_to` | 僅限Commerce Enterprise | | | 敏感 |
| 傳送RMA註解電子郵件副本至 | `sales_email/magento_rma_customer_comment/copy_to` | 僅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}

### Google API路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **銷售** > **Google API**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帳號 | `google/analytics/account` |  | | | 敏感 |

{style="table-layout:auto"}

## 進階類別

此區段列出&#x200B;**商店** >設定> **設定** > **進階**&#x200B;底下「管理員」中選項可用的變數名稱和設定路徑。

### 管理員敏感和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **進階** > **管理員**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自訂管理員URL | `admin/url/custom` |  | | | 敏感 |
| 自訂管理路徑 | `admin/url/custom_path` |  | | | 敏感 |

{style="table-layout:auto"}

### 系統敏感路徑和系統特定路徑

這些組態值可在&#x200B;**存放區** >設定> **組態** > **進階** > **系統**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `system/magento_scheduled_import_export_log/error_email` |  | | | 敏感 |
| 存取清單 | `system/full_page_cache/varnish/access_list` |  |  | | 敏感 |
| 錯誤電子郵件寄件者 | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | 敏感 |

{style="table-layout:auto"}

### 開發人員敏感和系統特定路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **進階** > **開發人員**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允許的IP （逗號分隔） | `dev/restrict/allow_ips` |  | | 系統特定 | 敏感 |

{style="table-layout:auto"}

## 進階類別

此區段列出&#x200B;**商店** >設定> **設定** > **進階**&#x200B;底下「管理員」中選項可用的變數名稱和設定路徑。

### 系統路徑

這些組態值可在&#x200B;**存放區** >設定> **組態** > **進階** > **系統**&#x200B;的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主機 | `system/smtp/host` |  | | 系統特定 | 敏感 |
| 連線埠(25) | `system/smtp/port` |  | | 系統特定 | 敏感 |
| 後端主機 | `system/full_page_cache/varnish/backend_host` |  | | 系統特定 | 敏感 |
| 後端連線埠 | `system/full_page_cache/varnish/backend_port` |  | | 系統特定 | 敏感 |

{style="table-layout:auto"}

### 開發人員路徑

這些設定值可在&#x200B;**商店** >設定> **設定** > **進階** > **開發人員**&#x200B;中的管理員中使用。

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將JS錯誤記錄到工作階段儲存金鑰 | `dev/js/session_storage_key` | ![不僅Commerce](/help/assets/configuration/red-x.png) | | 系統特定 | |

{style="table-layout:auto"}

## 付款敏感路徑和系統特定路徑

此區段列出&#x200B;**商店** >設定> **設定** > **銷售** > **付款**&#x200B;底下「管理員」中選項可用的變數名稱和設定路徑。

### 一般變數

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ |
|--------------|--------------|--------------|--------------|
| 商戶國家 | `paypal/general/merchant_country` |  | 敏感 |

{style="table-layout:auto"}

>[!INFO]
>
>您對此變數的選擇決定您可以使用哪些[國際路徑](#international-paths)。

### PayPal敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 與PayPal商家帳戶相關聯的電子郵件（選用） | `paypal/general/business_account` |  | | | 敏感 |
| 商家帳戶ID | `payment/paypal_express/merchant_id` |  | | | 敏感 |
| 發行者ID | `payment/paypal_express_bml/publisher_id` |  | | | 敏感 |
| 密碼 | `paypal/fetch_reports/ftp_password` |  | 已加密 | | 敏感 |
| 登入 | `paypal/fetch_reports/ftp_login` |  | 已加密 | | 敏感 |
| 自訂端點主機名稱或IP位址 | `paypal/fetch_reports/ftp_ip` |  | | 系統特定 | 敏感 |
| 沙箱模式 | `paypal/fetch_reports/ftp_sandbox` |  | | 系統特定 | |
| 偵錯模式 | `payment/paypal_express/debug` |  | | 系統特定 | |
| 偵錯模式 | `payment/paypal_billing_agreement/debug` |  | | 系統特定 | |
| SFTP認證 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payflow Pro敏感和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_advanced/user` |  | 已加密 | | 敏感 |
| 密碼 | `payment/payflow_advanced/pwd` |  | 已加密 | | 敏感 |
| 自訂路徑 | `paypal/fetch_reports/ftp_path` |  | | 系統特定 | 敏感 |
| 使用者 | `payment/payflowpro/user` |  | 已加密 | | 敏感 |
| 密碼 | `payment/payflowpro/pwd` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment/payflowpro/sandbox_flag` |  | | 系統特定 | |
| 合作夥伴 | `payment/payflowpro/partner` |  | | | 敏感 |
| Proxy主機 | `payment/payflowpro/proxy_host` |  | | 系統特定 | 敏感 |
| Proxy連線埠 | `payment/payflowpro/proxy_port` |  | | 系統特定 | 敏感 |
| 偵錯模式 | `payment/payflowpro/debug` |  | | 系統特定 | |
| SFTP認證 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | 系統特定 | |
| 信用卡設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payflow連結敏感和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_link/user` |  | 已加密 | | 敏感 |
| 密碼 | `payment/payflow_link/pwd` |  | 已加密 | | 敏感 |
| 測試模式 | `payment/payflow_link/sandbox_flag` |  | | 系統特定 | |
| 使用Proxy | `payment/payflow_link/use_proxy` |  | | 系統特定 | |
| Proxy主機 | `payment/payflow_link/proxy_host` |  | | 系統特定 | |
| Proxy連線埠 | `payment/payflow_link/proxy_port` |  |  | 系統特定 | |
| 偵錯模式 | `payment/payflow_link/debug` |  | | 系統特定 | |
| 用於取消URL和傳回URL的URL方法 | `payment/payflow_link/url_method` |  | | 系統特定 | |
| 偵錯模式 | `payment/payflow_express/debug` |  | | 系統特定 | |
| SFTP認證 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payments Pro敏感和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API使用者名稱 | `paypal/wpp/api_username` |  | 已加密 | | 敏感 |
| API密碼 | `paypal/wpp/api_password` |  | 已加密 | | 敏感 |
| API簽章 | `paypal/wpp/api_signature` |  | 已加密 | | 敏感 |
| API憑證 | `paypal/wpp/api_cert` |  | | | 敏感 |
| Proxy主機 | `paypal/wpp/proxy_host` |  | | 系統特定 | 敏感 |
| Proxy連線埠 | `paypal/wpp/proxy_port` |  | | 系統特定 | 敏感 |
| 沙箱模式 | `paypal/wpp/sandbox_flag` |  | | 系統特定 | |
| SFTP認證 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payments Pro託管敏感和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 偵錯模式 | `payment/hosted_pro/debug` |  | | 系統特定 | |
| SFTP認證 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### Braintree敏感和系統特定路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商家ID | `payment/braintree/merchant_id` |  | | | 敏感 |
| 公開金鑰 | `payment/braintree/public_key` |  | 已加密 | | 敏感 |
| 私密金鑰 | `payment/braintree/private_key` |  | 已加密 | | 敏感 |
| 商家帳戶ID | `payment/braintree/merchant_account_id` |  | | | 敏感 |
| 帳戶商家ID | `payment/braintree/kount_id` |  | | | 敏感 |
| 覆寫商家名稱 | `payment/braintree_paypal/merchant_name_override` |  | | | 敏感 |
| 電話 | `payment/braintree/descriptor_phone` |  | | | 敏感 |
| URL | `payment/braintree/descriptor_url` |  | | 系統特定 | |

{style="table-layout:auto"}

### 支票/匯票路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 傳送支票到 | `payment/checkmo/mailing_address` |  | | | 敏感 |
| 傳送支票到 | `payment_us/checkmo/mailing_address` |  | | | 敏感 |

{style="table-layout:auto"}

### 國際路徑

| 名稱 | 設定路徑 | Commerce版本支援 | 已加密？ | 系統專用？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 交易金鑰 | `payment_au/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_au/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_au/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_au/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_au/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_au/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_au/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_au/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_au/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_au/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 沙箱模式 | `payment_au/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_au/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_au/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_au/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_au/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_au/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_au/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_es/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_es/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_es/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_es/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_es/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_es/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_es/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_es/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_es/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_es/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 交易的MD5密碼 | `payment_es/worldpay/md5_secret` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 偵錯 | `payment_es/worldpay/debug` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_es/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_es/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_es/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_es/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_es/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_es/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_es/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_nz/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_nz/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_nz/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 測試模式 | `payment_nz/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 測試模式 | `payment_nz/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_nz/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_nz/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_nz/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_nz/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_nz/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 沙箱API密碼 | `payment_nz/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_nz/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment/payflow_advanced/sandbox_flag` |  | | 系統特定 | |
| Proxy主機 | `payment/payflow_advanced/proxy_host` |  | | 系統特定 | 敏感 |
| Proxy連線埠 | `payment/payflow_advanced/proxy_port` |  | | 系統特定 | |
| 偵錯模式 | `payment/payflow_advanced/debug` |  | | 系統特定 | |
| 用於取消URL和傳回URL的URL方法 | `payment/payflow_advanced/url_method` |  | | 系統特定 | |
| 測試模式 | `payment_us/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_us/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_us/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 存取金鑰 | `payment_us/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_us/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_us/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 測試模式 | `payment_us/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_us/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_us/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_us/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_us/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_us/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_us/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_us/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | |
| 測試模式 | `payment_gb/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 測試模式 | `payment_gb/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_gb/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 測試模式 | `payment_gb/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_gb/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_gb/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_gb/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_gb/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_gb/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_gb/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_gb/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_de/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_de/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_de/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_de/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 交易金鑰 | `payment_de/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_de/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_de/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_de/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 付款回應密碼 | `payment_de/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_de/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 偵錯 | `payment_de/worldpay/debug` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_de/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_de/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_de/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_de/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_de/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_de/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_de/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_other/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_other/authorizenet_directpost/test` |  | | 系統特定 | 敏感 |
| 閘道URL | `payment_other/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_other/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | |
| 交易金鑰 | `payment_other/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_other/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_other/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 新訂單狀態 | `payment_other/cybersource/order_status` | 僅限Commerce Enterprise | | 系統特定 | |
| 測試模式 | `payment_other/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_other/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_other/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_other/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_other/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_other/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_other/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_other/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_other/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_other/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_other/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_ca/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_ca/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_ca/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_ca/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_ca/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_ca/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 新訂單狀態 | `payment_ca/cybersource/order_status` | 僅限Commerce Enterprise | | | |
| 測試模式 | `payment_ca/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_ca/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | |
| 遠端管理員授權密碼 | `payment_ca/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_ca/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_ca/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_ca/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_ca/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_ca/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_ca/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 沙箱API密碼 | `payment_ca/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_ca/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_hk/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_hk/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_hk/authorizenet_directpost/cgi_url` |  | | | 敏感 |
| 交易詳細資料URL | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_hk/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_hk/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_hk/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_hk/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 付款回應密碼 | `payment_hk/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_hk/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_hk/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 即時API金鑰 | `payment_hk/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 即時API密碼 | `payment_hk/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_hk/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_hk/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_hk/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_hk/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_jp/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_jp/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_jp/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_jp/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_jp/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_jp/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 新訂單狀態 | `payment_jp/cybersource/order_status` | 僅限Commerce Enterprise | | 系統特定 | |
| 測試模式 | `payment_jp/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_jp/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_jp/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_jp/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_jp/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_jp/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_jp/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_jp/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_jp/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_jp/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_jp/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_fr/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_fr/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_fr/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_fr/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_fr/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_fr/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_fr/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_fr/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_fr/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_fr/worldpay/sandbox_flag` | 僅限Commerce Enterprise |  | 系統特定 | |
| 沙箱模式 | `payment_fr/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_fr/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_fr/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_fr/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_fr/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_fr/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_fr/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 交易金鑰 | `payment_it/authorizenet_directpost/trans_key` |  | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_it/authorizenet_directpost/test` |  | | 系統特定 | |
| 閘道URL | `payment_it/authorizenet_directpost/cgi_url` |  | | 系統特定 | 敏感 |
| 交易詳細資料URL | `payment_it/authorizenet_directpost/cgi_url_td` |  | | 系統特定 | 敏感 |
| 交易金鑰 | `payment_it/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 存取金鑰 | `payment_it/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 秘密金鑰 | `payment_it/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 測試模式 | `payment_it/cybersource/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 付款回應密碼 | `payment_it/worldpay/response_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 遠端管理員授權密碼 | `payment_it/worldpay/auth_password` | 僅限Commerce Enterprise | | 系統特定 | 敏感 |
| 測試模式 | `payment_it/worldpay/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 沙箱模式 | `payment_it/eway/sandbox_flag` | 僅限Commerce Enterprise | | 系統特定 | |
| 即時API金鑰 | `payment_it/eway/live_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時API密碼 | `payment_it/eway/live_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 即時使用者端加密金鑰 | `payment_it/eway/live_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API金鑰 | `payment_it/eway/sandbox_api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱API密碼 | `payment_it/eway/sandbox_api_password` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| 沙箱使用者端加密金鑰 | `payment_it/eway/sandbox_encryption_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| API金鑰 | `fraud_protection/signifyd/api_key` | 僅限Commerce Enterprise | 已加密 | 系統特定 | 敏感 |
| API URL | `fraud_protection/signifyd/api_url` | 僅限Commerce Enterprise |  | 系統特定 | 敏感 |
| SFTP認證 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| API登入ID | `payment_au/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_au/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_au/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 遠端管理安裝ID | `payment_au/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_au/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 傳送支票到 | `payment_es/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_es/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_es/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_es/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_es/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_es/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 遠端管理安裝ID | `payment_es/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | | | | | |
| SFTP認證 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| API登入ID | `payment_nz/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_nz/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_nz/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_nz/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易金鑰 | `payment_nz/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_nz/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 存取金鑰 | `payment_nz/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 秘密金鑰 | `payment_nz/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_nz/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 付款回應密碼 | `payment_nz/worldpay/response_password` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_nz/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理員授權密碼 | `payment_nz/worldpay/auth_password` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_nz/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |
| API登入ID | `payment_us/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 交易金鑰 | `payment_us/authorizenet_directpost/trans_key` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_us/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_us/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_us/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易金鑰 | `payment_us/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_us/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_us/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 付款回應密碼 | `payment_us/worldpay/response_password` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_us/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理員授權密碼 | `payment_us/worldpay/auth_password` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_us/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP認證 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 傳送支票到 | `payment_gb/checkmo/mailing_address` |  | | | 敏感 |
| 商家ID | `payment_gb/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易金鑰 | `payment_gb/cybersource/transaction_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_gb/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 存取金鑰 | `payment_gb/cybersource/access_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 秘密金鑰 | `payment_gb/cybersource/secret_key` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| API登入ID | `payment_gb/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 交易金鑰 | `payment_gb/authorizenet_directpost/trans_key` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_gb/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | 敏感 |
| 安裝ID | `payment_gb/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 付款回應密碼 | `payment_gb/worldpay/response_password` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_gb/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理員授權密碼 | `payment_gb/worldpay/auth_password` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_de/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_de/checkmo/mailing_address` |  | | | 敏感 |
| 商家ID | `payment_de/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_de/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| API登入ID | `payment_de/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_de/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_de/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 安裝ID | `payment_de/worldpay/installation_id` | 僅限Commerce Enterprise | | | |
| 遠端管理安裝ID | `payment_de/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_de/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP認證 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_other/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_other/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_other/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 新訂單狀態 | `payment_other/authorizenet_directpost/order_status` |  | | | 敏感 |
| 商戶電子郵件 | `payment_other/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_other/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_other/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_other/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_other/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_other/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_ca/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_ca/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_ca/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 新訂單狀態 | `payment_ca/authorizenet_directpost/order_status` |  | | | 敏感 |
| 傳送電子郵件給客戶 | `payment_ca/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_ca/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_ca/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_ca/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_ca/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_ca/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_ca/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP認證 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_hk/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_hk/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_hk/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_hk/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_hk/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_hk/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_hk/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_hk/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_hk/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_hk/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| 簽章欄位 | `payment_hk/worldpay/signature_fields` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_jp/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_jp/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_jp/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_jp/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_jp/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_jp/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_jp/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_jp/worldpay/installation_id` | 僅限Commerce Enterprise | | | |
| 遠端管理安裝ID | `payment_jp/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_jp/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| 簽章欄位 | `payment_jp/worldpay/signature_fields` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_fr/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_fr/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_fr/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_fr/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_fr/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_fr/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_fr/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_fr/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_fr/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_fr/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |
| 簽章欄位 | `payment_fr/worldpay/signature_fields` | 僅限Commerce Enterprise | | | 敏感 |
| SFTP認證 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP認證 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 將支票支付給 | `payment_it/checkmo/payable_to` |  | | | 敏感 |
| 傳送支票到 | `payment_it/checkmo/mailing_address` |  | | | 敏感 |
| API登入ID | `payment_it/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 傳送電子郵件給客戶 | `payment_it/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商戶電子郵件 | `payment_it/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_it/cybersource/merchant_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 設定檔ID | `payment_it/cybersource/profile_id` | 僅限Commerce Enterprise | 已加密 | | 敏感 |
| 安裝ID | `payment_it/worldpay/installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 遠端管理安裝ID | `payment_it/worldpay/admin_installation_id` | 僅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密碼 | `payment_it/worldpay/md5_secret` | 僅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}
