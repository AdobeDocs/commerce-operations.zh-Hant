---
title: B2B擴展配置路徑參考
description: 請參見與B2B相關的配置值清單。
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# B2B擴展配置路徑參考

_這適用於安裝了B2B的Adobe Commerce實例。_

本主題列出了Commerce Enterprise B2B擴展的配置路徑。 的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用配置檔案， `app/etc/config.php`，它應該在原始碼管理中。

>[!INFO]
>
>此引用清單 _僅_ 為Adobe Commerce提供B2B獨有的配置路徑。 此擴展包含Adobe Commerce的所有配置路徑。

有關這些配置路徑，請參閱：

- [付款配置路徑](config-reference-payment.md)
- [敏感和特定於系統的配置路徑參考](config-reference-sens.md)

要可選地覆蓋任何配置設定或設定敏感設定，請參閱 [使用環境變數覆蓋配置設定](override-config-settings.md#environment-variables)。

## 一般類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL General]**。

### B2B功能路徑

這些配置值在中的管理中可用 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 啟用公司 | `btob/website_configuration/company_active` |  |  |  |
| 啟用共用目錄 | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| 啟用B2B報價 | `btob/website_configuration/negotiablequote_active` |  |  |  |
| 啟用快速訂單 | `btob/website_configuration/quickorder_active` |  |  |  |
| 啟用申請清單 | `btob/website_configuration/requisition_list_active` |  |  |  |
| 適用的付款方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| 付款方法 | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style="table-layout:auto"}

## 客戶類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**。

### 公司配置路徑

這些配置值在中的管理中可用 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|
| 允許從店面註冊公司 | `company/general/allow_company_registration` |  |  |  |
| 公司註冊電子郵件收件人 | `company/email/company_registration` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將公司註冊電子郵件副本發送到 | `company/email/company_registration_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發送電子郵件複製方法 | `company/email/company_copy_method` |  |  |  |
| 預設公司註冊電子郵件 | `company/email/company_notify_admin_template` |  |  |  |
| 與客戶相關的電子郵件 | `company/email/heading_customer` |  |  |  |
| 預設銷售代表分配的電子郵件 | `company/email/customer_sales_representative_template` |  |  |  |
| 預設將公司分配給客戶電子郵件 | `company/email/customer_company_customer_assign_template` |  |  |  |
| 預設分配公司管理電子郵件 | `company/email/customer_assign_super_user_template` |  |  |  |
| 預設公司管理員非活動電子郵件 | `company/email/customer_inactivate_super_user_template` |  |  |  |
| 預設公司管理員更改為成員電子郵件 | `company/email/customer_remove_super_user_template` |  |  |  |
| 預設客戶狀態有效電子郵件 | `company/email/customer_account_activated_template` |  |  |  |
| 預設客戶狀態非活動電子郵件 | `company/email/customer_account_locked_template` |  |  |  |
| 公司狀態更改 | `company/email/heading_company_status` |  |  |  |
| 公司狀態更改電子郵件收件人 | `company/email/company_status_change` |  |  |  |
| 將公司狀態更改電子郵件副本發送到 | `company/email/company_status_change_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發送電子郵件複製方法 | `company/email/company_status_copy_method` |  |  |  |
| 預設公司狀態更改為活動1電子郵件 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| 預設公司狀態更改為活動2電子郵件 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| 預設公司狀態更改為拒絕的電子郵件 | `company/email/company_status_rejected_template` |  |  |  |
| 預設公司狀態更改為阻止的電子郵件 | `company/email/company_status_blocked_template` |  |  |  |
| 預設公司狀態更改為待定審批電子郵件 | `company/email/company_status_pending_approval_template` |  |  |  |
| 公司貸項 | `company/email/heading_company_credit` |  |  |  |
| 公司信用更改電子郵件發件人 | `company/email/company_credit_change` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將公司信用更改電子郵件副本發送到 | `company/email/company_credit_change_copy` |  |  |  |
| 發送電子郵件複製方法 | `company/email/company_credit_copy_method` |  |  |  |
| 已分配的電子郵件模板 | `company/email/credit_allocated_email_template` |  |  |  |
| 已更新的電子郵件模板 | `company/email/credit_updated_email_template` |  |  |  |
| 報銷電子郵件模板 | `company/email/credit_reimbursed_email_template` |  |  |  |
| 已退款電子郵件模板 | `company/email/credit_refunded_email_template` |  |  |  |
| 已還原電子郵件模板 | `company/email/credit_reverted_email_template` |  |  |  |

{style="table-layout:auto"}

### 申請清單路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **客戶** > **申請清單**。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 申請清單數 | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style="table-layout:auto"}

## 銷售類別

本節列出了Admin中的變數名稱和可用於以下選項的配置路徑： **商店** >設定> **配置** > **銷售**。

### 銷售電子郵件路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **銷售電子郵件**。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已啟用 | `sales_email/quote/enabled` |  |  |  |
| 更新的報價模板（至採購員） | `sales_email/quote/updated_buyer_template` |  |  |  |
| 拒絕報價模板（至採購員） | `sales_email/quote/declined_buyer_template` |  |  |  |
| 新報價模板（銷售商） | `sales_email/quote/new_seller_template` |  |  |  |
| 更新的報價模板（銷售商） | `sales_email/quote/updated_seller_template` |  |  |  |
| 報價到期（48小時後） | `sales_email/quote/expire_two_days_template` |  |  |  |
| 報價到期（24小時後） | `sales_email/quote/expire_one_day_template` |  |  |  |
| 過期日期重置 | `sales_email/quote/expire_reset_template` |  |  |  |
| 將報價電子郵件副本發送到 | `sales_email/quote/copy_to` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發送報價電子郵件複製方法 | `sales_email/quote/copy_method` |  |  |  |

{style="table-layout:auto"}

### 引號路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **報價**。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小金額消息 | `quote/general/minimum_amount_message` |  |  |  |
| 預設到期期 | `quote/general/default_expiration_period` |  |  |  |
| 用於上載的檔案格式 | `quote/attached_files/file_formats` |  |  |  |
| 最大檔案大小 | `quote/attached_files/maximum_file_size` |  |  |  |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小金額消息 | `quote/general/minimum_amount_message` |  |  |  |
| 預設到期期 | `quote/general/default_expiration_period` |  |  |  |
| 用於上載的檔案格式 | `quote/attached_files/file_formats` |  |  |  |
| 最大檔案大小 | `quote/attached_files/maximum_file_size` |  |  |  |

{style="table-layout:auto"}

## 付款方法路徑

這些配置值在中的管理中可用 **商店** >設定> **配置** > **銷售** > **付款方法**。

>[!INFO]
>
>可用路徑由您選擇的商家國家/地區決定。

| 名稱 | 配置路徑 | 加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已啟用 | `payment/au/companycredit/active` |  |  |  |
| 標題 | `payment/au/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/au/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/au/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/au/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/au/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/au/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/au/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/es/companycredit/active` |  |  |  |
| 標題 | `payment/es/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/es/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/es/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/es/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/es/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/es/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/es/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/companycredit/active` |  |  |  |
| 標題 | `payment/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/nz/companycredit/active` |  |  |  |
| 標題 | `payment/nz/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/nz/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/nz/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/nz/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/nz/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/nz/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/nz/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/us/companycredit/active` |  |  |  |
| 標題 | `payment/us/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/us/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/us/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/us/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/us/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/us/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/us/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/gb/companycredit/active` |  |  |  |
| 標題 | `payment/gb/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/gb/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/gb/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/gb/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/gb/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/gb/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/gb/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/de/companycredit/active` |  |  |  |
| 標題 | `payment/de/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/de/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/de/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/de/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/de/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/de/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/de/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/other/companycredit/active` |  |  |  |
| 標題 | `payment/other/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/other/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/other/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/other/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/other/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/other/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/other/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/ca/companycredit/active` |  |  |  |
| 標題 | `payment/ca/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/ca/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/ca/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/ca/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/ca/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/ca/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/ca/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/hk/companycredit/active` |  |  |  |
| 標題 | `payment/hk/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/hk/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/hk/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/hk/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/hk/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/hk/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/hk/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/jp/companycredit/active` |  |  |  |
| 標題 | `payment/jp/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/jp/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/jp/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/jp/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/jp/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/jp/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/jp/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/fr/companycredit/active` |  |  |  |
| 標題 | `payment/fr/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/fr/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/fr/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/fr/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/fr/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/fr/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/fr/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/it/companycredit/active` |  |  |  |
| 標題 | `payment/it/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/it/companycredit/order_status` |  |  |  |
| 從適用國家/地區付款 | `payment/it/companycredit/allowspecific` |  |  |  |
| 特定國家/地區的付款 | `payment/it/companycredit/specificcountry` |  |  |  |
| 最小訂單合計 | `payment/it/companycredit/min_order_total` |  |  |  |
| 最大訂單總數 | `payment/it/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/it/companycredit/sort_order` |  |  |  |

{style="table-layout:auto"}
