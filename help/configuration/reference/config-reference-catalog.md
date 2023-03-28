---
title: 目錄配置路徑參考
description: 請參閱目錄配置值清單。
source-git-commit: e4b7ea70b96143629b245409537459ad259393e0
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---


# 目錄配置路徑參考

本節列出「管理員」下方之選項可用的變數名稱和設定路徑 **商店** >設定> **設定** > **目錄**.

此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，應在原始碼控制中。 要選擇覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數來覆寫組態設定](override-config-settings.md#environment-variables). 本主題說明 _not_ 清單 [敏感值和系統特定值](config-reference-sens.md).

## 目錄路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **目錄**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| SKU遮色片 | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 元標題遮色片 | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 中繼關鍵字的遮罩 | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 元描述遮罩 | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清單模式 | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 網格上每頁產品允許的值 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 網格預設值上的每頁產品數 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清單允許值上的每頁產品數 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清單預設值上的每頁產品數 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產品清單排序依據 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每頁允許所有產品 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用固定目錄類別 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用平面目錄產品 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每個產品的色票 | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許來賓編寫評論 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產品價格變更時允許警報 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 價格警報電子郵件範本 | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許在產品重新庫存時發出警報 | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 庫存警報電子郵件範本 | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 警報電子郵件寄件者 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件寄件者 | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件範本 | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示當前 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設最近查看的產品計數 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設最近比較的產品計數 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動啟動基本視頻 | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示相關視頻 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動重新啟動視頻 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目錄價格範圍 | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設產品價格 | `catalog/price/default_product_price` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示產品計數 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 價格導航步驟計算 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設價格導航步驟 | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將價格間隔顯示為單價 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大價格間隔數 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔除數限制 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大深度 | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小查詢長度 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大查詢長度 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 搜尋引擎 | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr伺服器超時 | `catalog/search/solr_server_timeout` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 索引模式 | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用搜尋建議 | `catalog/search/search_suggestion_enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 搜尋建議計數 | `catalog/search/search_suggestion_count` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示每個建議的結果計數 | `catalog/search/search_suggestion_count_results_enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 啟用搜尋Recommendations | `catalog/search/search_recommendations_enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 搜尋Recommendations計數 | `catalog/search/search_recommendations_count` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示每個建議的結果計數 | `catalog/search/search_recommendations_count_results_enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 要符合的最低詞語 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產生「類別/產品」URL重新寫入 | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 熱門搜尋詞 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產品URL尾碼 | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 類別URL尾碼 | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產品URL的使用類別路徑 | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果URL索引鍵變更，請為URL建立永久重新導向 | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁面標題分隔符號 | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 對類別使用標準連結中繼標籤 | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為產品使用標準連結中繼標籤 | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用 | `catalog/magento_catalogpermissions/enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 允許瀏覽類別 | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 客戶群組 | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 登陸頁面 | `catalog/magento_catalogpermissions/restricted_landing_page` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示產品價格 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 客戶群組 | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 允許添加到購物車 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 客戶群組 | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 不允許目錄搜索依據 | `catalog/magento_catalogpermissions/deny_catalog_search` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 啟用下載的訂單項狀態 | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設的下載次數上限 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可共用 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設範例標題 | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設連結標題 | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在新視窗中開啟連結 | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用Content-Disposition | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果購物車包含可下載的項目，則停用訪客結帳 | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用JavaScript日曆 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日期欄位順序 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時間格式 | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 年範圍 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用目錄事件功能 | `catalog/magento_catalogevent/enabled` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 在店面上啟用目錄事件Widget | `catalog/magento_catalogevent/lister_output` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 事件滑桿Widget中要顯示的事件數 | `catalog/magento_catalogevent/lister_widget_limit` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 事件滑桿Widget中每次點按捲動的事件 | `catalog/magento_catalogevent/lister_widget_scroll` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 相關產品清單中的最大產品數 | `catalog/magento_targetrule/related_position_limit` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示相關產品 | `catalog/magento_targetrule/related_position_behavior` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 相關產品清單中產品的輪換模式 | `catalog/magento_targetrule/related_rotation_mode` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 交叉銷售產品清單中的最大產品數 | `catalog/magento_targetrule/crosssell_position_limit` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示交叉銷售產品 | `catalog/magento_targetrule/crosssell_position_behavior` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 交叉銷售產品清單中產品的輪換模式 | `catalog/magento_targetrule/crosssell_rotation_mode` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 追加銷售產品清單中的最大產品數 | `catalog/magento_targetrule/upsell_position_limit` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顯示向上銷售產品 | `catalog/magento_targetrule/upsell_position_behavior` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 向上銷售產品清單中產品的輪換模式 | `catalog/magento_targetrule/upsell_rotation_mode` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 庫存路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **庫存**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| 下訂單時減少庫存 | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在取消訂單時將物料的狀態設定為庫存 | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示無庫存產品 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 僅X左臨界值 | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上以庫存顯示產品可用性 | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 與目錄同步 | `cataloginventory/options/synchronize_with_catalog` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 管理庫存 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 延交訂單 | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用延期庫存更新 | `cataloginventory/item_options/use_deferred_stock_update` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 購物車中允許的最大數量 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無存貨臨界值 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 購物車中允許的最小數量 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 通知以下數量 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用數量增量 | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 數量增加 | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動將貸項通知單項退回至庫存 | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同步執行 | `cataloginventory/bulk_operations/async` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 非同步批次大小 | `cataloginventory/bulk_operations/batch_size` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 提供者 | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算模式 | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 值 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 視覺採購員路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **Visual Stulder**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| 類別規則的可見屬性 | `visualmerchandiser/options/smart_attributes` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 最小庫存閾值 | `visualmerchandiser/options/minimum_stock_threshold` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 顏色屬性代碼 | `visualmerchandiser/options/color_attribute_code` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |
| 色彩順序 | `visualmerchandiser/options/color_order` | ![僅限商務](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML Sitemap路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **XML Sitemap**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| 頻率 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先順序 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先順序 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將影像新增至Sitemap | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先順序 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件寄件者 | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件範本 | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每個檔案的最大URL數 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 檔案大小上限 | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用提交至Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS饋送路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **RSS源**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| 啟用RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新產品 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特殊產品 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 抵用券/折扣 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頂級類別 | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客戶訂單狀態通知 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 傳送電子郵件給朋友路徑

這些設定值可在 **商店** >設定> **設定** > **目錄** > **發電子郵件給朋友**.

| 名稱 | 設定路徑 | 只有商務？ |
|--------------|--------------|--------------|
| 已啟用 | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 選取電子郵件範本 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許來賓 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大收件者 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在1小時內發送的最大產品數 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發送限制 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
