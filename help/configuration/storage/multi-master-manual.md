---
title: 手動配置主資料庫
description: 請參閱手動配置拆分資料庫解決方案的指南。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---


# 手動配置主資料庫

{{ee-only}}

{{deprecate-split-db}}

如果Commerce應用程式已在生產環境中，或者您已安裝自定義代碼或元件，則可能需要手動配置拆分資料庫。 繼續操作之前，請聯絡Adobe Commerce支援，查看在您的案例中是否需要。

手動拆分資料庫涉及：

- 建立結帳和訂單管理系統(OMS)資料庫
- 運行一系列SQL指令碼，這些指令碼包括：

   - 放置外鍵
   - 備份銷售和報價資料庫表
   - 將表從主資料庫移動到銷售資料庫和報價資料庫

>[!WARNING]
>
>如果任何自定義代碼使用JOIN和銷售資料庫和報價資料庫中的表，則您 _不能_ 使用拆分資料庫。 如有疑問，請連絡任何自訂程式碼或擴充功能的作者，以確定其程式碼不使用JOIN。

本主題使用下列命名慣例：

- 主資料庫名稱為 `magento` 其用戶名和密碼均為 `magento`
- 報價資料庫名稱為 `magento_quote` 其用戶名和密碼均為 `magento_quote`

   引號資料庫也稱為 _簽出_ 資料庫。

- 銷售資料庫名稱為 `magento_sales` 其用戶名和密碼均為 `magento_sales`

   銷售資料庫也稱為OMS資料庫。

>[!INFO]
>
>本指南假設所有三個資料庫都與Commerce應用程式位於同一台主機上。 但是，資料庫的位置及其名稱由您決定。 我們希望這些範例能讓指示更容易遵循。

## 備份商務系統

Adobe強烈建議您備份當前的資料庫和檔案系統，以便在此過程中遇到問題時可以還原它。

**備份系統**:

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 輸入以下命令：

   ```bash
   magento setup:backup --code --media --db
   ```

1. 繼續下一節。

## 設定其他主資料庫

本節討論如何為銷售表和報價表建立資料庫實例。

**建立銷售和OMS報價資料庫**:

1. 以任何用戶身份登錄到資料庫伺服器。
1. 輸入以下命令以獲取MySQL命令提示：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 提示時的用戶密碼。
1. 按如下順序輸入以下命令，以建立名為 `magento_quote` 和 `magento_sales` 使用相同的用戶名和密碼：

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 輸入 `exit` 退出命令提示符。

1. 驗證資料庫，一次一個：

   報價資料庫：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   如果顯示MySQL監視器，則已正確建立資料庫。 如果顯示錯誤，請重複前面的命令。

1. 繼續下一節。

## 配置銷售資料庫

本節討論如何建立和運行SQL指令碼，這些指令碼會更改引號資料庫表並備份來自這些表的資料。

銷售資料庫表名稱的開頭為：

- `salesrule_`
- `sales_`
- `magento_sales_`
- 此 `magento_customercustomattributes_sales_flat_order` 表格也會受到影響

>[!INFO]
>
>本節包含具有特定資料庫表名的指令碼。 如果您已執行自定義操作，或者要在對表執行操作之前查看完整的表清單，請參閱 [參考指令碼](#reference-scripts).

如需詳細資訊，請參閱：

- [建立銷售資料庫SQL指令碼](#create-sales-database-sql-scripts)
- [備份銷售資料](#back-up-sales-data)

### 建立銷售資料庫SQL指令碼

在您登入Commerce伺服器時，使用者可存取的位置中建立下列SQL指令碼。 例如，如果您以 `root`，您可以在 `/root/sql-scripts` 目錄。

#### 刪除外鍵

此指令碼從銷售資料庫中刪除引用非銷售表的外鍵。

建立以下指令碼，並為其命名，如 `1_foreign-sales.sql`. 取代 `<your main DB name>` 和資料庫的名稱。

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### 配置銷售資料庫

運行前一指令碼：

1. 以 `root` 或管理用戶：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，按如下方式運行指令碼：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. 指令碼執行後，請輸入 `exit`.

### 備份銷售資料

本節討論如何從主Commerce資料庫備份銷售表，以便在單獨的銷售資料庫中還原這些表。

如果您目前位於 `mysql>` 提示，輸入 `exit` 返回命令shell。

執行下列 `mysqldump` 命令shell中的一個命令。 在每個中，取代下列項目：

- `<your database root username>` 資料庫根用戶的名稱
- `<your database root user password>` 使用者密碼
- `<your main Commerce DB name>` 名稱為Commerce資料庫
- `<path>` 具有可寫檔案系統路徑

#### 指令碼1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### 指令碼2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### 指令碼3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### 指令碼4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 恢復銷售資料

此指令碼將還原報價資料庫中的銷售資料。

#### NDB要求

如果您使用 [網路資料庫(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 群集：

1. 在轉儲檔案中將表從InnoDb轉換為NDB類型：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 從轉儲中刪除具有FULLTEXT鍵的行，因為NDB表不支援FULLTEXT。

#### 還原資料

運行以下命令：

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

其中

- `<your sales DB name>` 以及銷售資料庫的名稱。

   在本主題中，示例資料庫名稱為 `magento_sales`.

- `<root username>` 使用您的MySQL根用戶名
- `<root user password>` 使用者密碼
- 驗證您先前建立的備份檔案的位置(例如， `/var/sales.sql`)

## 配置報價資料庫

本節討論從銷售資料庫表中刪除外鍵和將表移動到銷售資料庫所需的任務。

>[!INFO]
>
>本節包含具有特定資料庫表名的指令碼。 如果您已執行自定義操作，或者要在對表執行操作之前查看完整的表清單，請參閱 [參考指令碼](#reference-scripts).

引號資料庫表名以開頭 `quote`. 此 `magento_customercustomattributes_sales_flat_quote` 和 `magento_customercustomattributes_sales_flat_quote_address` 表格也會受到影響

### 從引號表中刪除外鍵

此指令碼從引號表中刪除引用非引號表的外鍵。 取代 `<your main Commerce DB name>` 的名稱。

建立以下指令碼，並為其命名，如 `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

按如下方式運行指令碼：

1. 以根用戶或管理用戶身份登錄到MySQL資料庫：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql >` 提示，按如下方式運行指令碼：
   `source <path>/<script>.sql`

   例如，

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. 指令碼執行後，請輸入 `exit`.

### 備份報價表

本節討論如何從主資料庫備份引號表，並在引號資料庫中還原它們。

從命令提示符運行以下命令：

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB要求

如果您使用 [網路資料庫(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 群集：

1. 在轉儲檔案中將表從InnoDb轉換為NDB類型：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 從轉儲中刪除具有FULLTEXT鍵的行，因為NDB表不支援FULLTEXT。

### 將表還原到引號資料庫

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## 從資料庫中刪除銷售表和報價表

此指令碼銷售表和報價表來自商務資料庫。 取代 `<your main DB name>` 的名稱。

建立以下指令碼，並為其命名，如 `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

按如下方式運行指令碼：

1. 以根用戶或管理用戶身份登錄到MySQL資料庫：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，按如下方式運行指令碼：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. 指令碼執行後，請輸入 `exit`.

## 更新部署配置

手動拆分資料庫的最後一步是向Commerce的部署配置添加連接和資源資訊， `env.php`.

要更新部署配置，請執行以下操作：

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 備份部署配置：

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. 開啟 `<magento_root>/app/etc/env.php` 在文字編輯器中，並依照下節所述的准則加以更新。

### 更新資料庫連接

找出以開始的區塊 `'default'` (在 `'connection'`)和新增 `'checkout'` 和 `'sales'` 區段。 將範例值取代為適合您網站的值。

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### 更新資源

找出以開始的區塊 `'resource'` 新增 `'checkout'` 和 `'sales'` 區段如下：

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## 參考指令碼

本節提供可運行的指令碼，這些指令碼可打印受影響表的完整清單，而無需對其執行任何操作。 在手動拆分資料庫之前，可以使用它們查看哪些表受影響，如果使用自定義資料庫架構的擴展，這將非常有用。

要使用這些指令碼：

1. 使用本節中每個指令碼的內容建立SQL指令碼。
1. 在每個指令碼中，取代 `<your main DB name>` 的名稱。

   在本主題中，示例資料庫名稱為 `magento`.

1. 從 `mysql>` 提示為 `source <script name>`
1. 檢查輸出。
1. 將每個指令碼的結果複製到另一個SQL指令碼，移除垂直號字元(`|`)。
1. 從 `mysql>` 提示為 `source <script name>`.

   運行此第二個指令碼將執行主Commerce資料庫中的操作。

### 刪除外鍵（銷售表）

此指令碼從銷售資料庫中刪除引用非銷售表的外鍵。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### 刪除外鍵（引號表）

此指令碼從引號表中刪除引用非引號表的外鍵。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### 刪除銷售表

此指令碼從Commerce資料庫中刪除銷售表。

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### 刪除報價表

刪除所有以開頭的表 `quote_`.
