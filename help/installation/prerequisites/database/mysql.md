---
title: MySQL准則
description: 按照以下步驟安裝和配置MySQL和MariaDB，以在本地安裝Adobe Commerce和Magento Open Source。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# 常規MySQL准則

請參閱 [系統要求](../../system-requirements.md) 支援的MySQL版本。

Adobe _強烈_ 建議在設定資料庫時遵守以下標準：

* Adobe Commerce和Magento Open Source使用 [MySQL資料庫觸發器](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 以在重新編製索引期間改進資料庫訪問。 索引器模式設定為時建立這些 [計畫](../../../configuration/cli/manage-indexers.md#configure-indexers)。 該應用程式不支援資料庫中的任何自定義觸發器，因為自定義觸發器可能會導致與將來的Adobe Commerce和Magento Open Source版本不相容。
* 熟悉 [這些潛在的MySQL觸發器限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 才能繼續。
* 要增強資料庫安全狀態，請啟用 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式，用於防止儲存無效資料值，這可能導致不需要的資料庫交互。
* Adobe Commerce和Magento Open Source _不_ 支援基於MySQL陳述式的複製。 確保使用 _僅_ [基於行的複製](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html)。

>[!WARNING]
>
>Adobe Commerce目前使用 `CREATE TEMPORARY TABLE` 交易內的對帳單， [不相容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 與資料庫實現一起使用基於GTID的複製，如 [Google雲SQL第二代實例](https://cloud.google.com/sql/docs/features#differences)。 將MySQL for Cloud SQL 8.0作為替代方案。

>[!NOTE]
>
>如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的任務，請參閱 [設定遠程MySQL資料庫連接](mysql-remote.md)。

## 在Ubuntu上安裝MySQL

Adobe Commerce和Magento Open Source2.4需要全新安裝MySQL 8.0。有關在電腦上安裝MySQL的說明，請按照以下連結進行操作。

* [烏邦圖](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您希望進口大量產品，則可以 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 大於預設值16 MB。

>[!NOTE]
>
>預設值適用於雲基礎架構上的Adobe Commerce _和_ 內部項目。 Adobe Commerce雲基礎架構專業客戶必須開啟支援票證以增加 `max_allowed_packet` 值。 Adobe Commerce雲基礎架構啟動程式客戶可以通過更新 `/etc/mysql/mysql.cnf` 的子菜單。

要增加值，請開啟 `/etc/mysql/mysql.cnf` 在文本編輯器中查找 `max_allowed_packet`。 保存對 `mysql.cnf` 檔案，關閉文本編輯器，然後重新啟動MySQL(`service mysql restart`)。

要（可選）驗證您設定的值，請在 `mysql>` 提示：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然後， [配置資料庫實例](#configuring-the-database-instance)。

## MySQL 8更改

對於Adobe Commerce和2.4Magento Open Source，我們增加了對MySQL 8的支援。
本節介紹開發人員應注意的對MySQL 8的主要更改。

### 整數類型（填充）的已刪除寬度

MySQL 8.0.17中已棄用整數資料類型(TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT)的顯示寬度規範。在輸出中包含資料類型定義的語句不再顯示整數類型的顯示寬度，TINYINT(1)除外。 MySQL Connectors假定TINYINT(1)列以BOOLEAN列的形式產生。 這種例外使他們能夠繼續作出這種假設。

#### 示例

描述mysql 8.19上的admin_user

| 欄位 | 類型 | 空 | 鍵 | 預設 | 額外 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 用戶\_id | `int unsigned` | 否 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 是 |  | `NULL` |  |
| `lastname` | `varchar(32`) | 是 |  | `NULL` |  |
| `email` | `varchar(128)` | 是 |  | `NULL` |  |
| `username` | `varchar(40)` | 是 | 統一 | `NULL` |  |
| `password` | `varchar(255)` | 否 |  | `NULL` |  |
| `created` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 |  | `NULL` |  |
| `lognum` | `smallint unsigned` | 否 |  | `0` |  |

除 _TINYINT(1)_，應從 `db_schema.xml` 的子菜單。

有關詳細資訊，請參見 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature)。

### 預設ORDER BY行為

在8.0之前，條目按外鍵排序。 預設排序順序取決於使用的引擎。
如果代碼依賴於特定的排序，則始終指定排序順序。

### 已棄用的GROUP BY的ASC和DESC限定符

自MySQL 8.0.13起，已棄用 `ASC` 或 `DESC` 限定詞 `GROUP BY` 已刪除子句。 以前依賴的查詢 `GROUP BY` 排序可能會產生與以前的MySQL版本不同的結果。 要生成給定的排序順序，請提供 `ORDER BY` 。

## Commerce和MySQL 8

對Adobe Commerce和Magento Open Source進行了一些更改，以正確支援MySQL 8。

### 查詢和插入行為

Adobe Commerce和Magento Open Source通過在中設定SET SQL_MODE=&quot;禁用常規驗證行為 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`。 禁用驗證後，MySQL可能會截斷資料。 在MySQL中，查詢行為已更改： `Select * on my_table where IP='127.0.0.1'` 不再返回結果，因為IP地址現在正確地被視為字串，而不是整數。

## 從MySQL 5.7升級到MySQL 8

要將MySQL從5.7版正確更新到8版，必須按以下順序執行以下步驟：

1. 將Adobe Commerce或Magento Open Source升級到2.4.0。Test所有內容，確保系統按預期工作。
1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 進行資料庫備份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 將MySQL更新為版本8。
1. 將備份的資料導入MySQL。
1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 禁用維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

## 配置資料庫實例

本節討論如何為Adobe Commerce或Magento Open Source建立資料庫實例。 儘管建議使用新的資料庫實例，但您可以選擇安裝Adobe Commerce或與現有資料庫實例Magento Open Source。

配置MySQL資料庫實例：

1. 以任何用戶身份登錄到資料庫伺服器。
1. 轉到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 出現提示時的用戶密碼。
1. 按顯示的順序輸入以下命令以建立名為 `magento` 使用用戶名 `magento`:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. 輸入 `exit` 的子菜單。

1. 驗證資料庫：

   ```bash
   mysql -u magento -p
   ```

   如果顯示MySQL監視器，則已正確建立資料庫。 如果顯示錯誤，請重複前面的命令。

1. 如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的任務，請參閱 [設定遠程MySQL資料庫連接](mysql-remote.md)。

   我們建議您根據業務需要配置資料庫實例。 配置資料庫時，請牢記以下事項：

   * 索引器要求更高 `tmp_table_size` 和 `max_heap_table_size` 值（例如64 M）。 如果配置 `batch_size` 參數時，可以調整該值以及表大小設定，以提高索引器效能。 請參閱 [優化指南](../../../performance/configuration.md) 的子菜單。

   * 為獲得最佳效能，請確保所有MySQL和Adobe Commerce或Magento Open Source索引表都保留在記憶體中(例如，配置 `innodb_buffer_pool_size`)。

   * 與其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新編製索引需要更多時間。 請參閱 [配置最佳做法](../../../performance/configuration.md#indexers)。

1. 用於MySQL `TIMESTAMP` 欄位將遵循應用程式的聲明性模式體系結構（系統變數）所需的首選項和組合 `explicit_defaults_for_timestamp` 必須設定為 `on`。

   引用：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [瑪麗亞](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未啟用此設定， `bin/magento setup:db:status` 總是報告 `Declarative Schema is not up to date`。

>[!NOTE]
>
>的 `explicit_defaults_for_timestamp` 設定已棄用。 此設定控制將來在MySQL發行版中刪除的不建議使用的TIMESTAMP行為。 刪除這些行為時， `explicit_defaults_for_timestamp` 也會刪除設定。

>[!WARNING]
>
>對於Adobe Commerce的雲基礎架構項目， `explicit_defaults_for_timestamp` 將MySQL(MariaDB)預設設定為 _關閉_。

{{$include /help/_includes/maria-db-config.md}}
