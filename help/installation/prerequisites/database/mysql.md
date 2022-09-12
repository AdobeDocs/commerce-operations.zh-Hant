---
title: MySQL准則
description: 請按照以下步驟安裝和配置MySQL和MariaDB，以在本地安裝Adobe Commerce和Magento Open Source。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# 一般MySQL指南

請參閱 [系統需求](../../system-requirements.md) 以了解MySQL的支援版本。

Adobe _強烈_ 建議您在設定資料庫時遵守下列標準：

* Adobe Commerce和Magento Open Source使用 [MySQL資料庫觸發器](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 在重新索引期間改進資料庫訪問。 當索引器模式設定為 [排程](../../../configuration/cli/manage-indexers.md#configure-indexers). 應用程式不支援資料庫中的任何自訂觸發程式，因為自訂觸發程式可能會造成與未來Adobe Commerce和Magento Open Source版本不相容。
* 熟悉 [這些潛在的MySQL觸發器限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 之後繼續。
* 要增強資料庫安全態勢，請啟用 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式，以防止儲存無效的資料值，這可能會導致不需要的資料庫交互。
* Adobe Commerce和Magento Open Sourcedo _not_ 支援基於MySQL陳述式的複製。 請務必使用 _僅限_ [行複製](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce和Magento Open Source目前使用 `CREATE TEMPORARY TABLE` 交易內的報表，即 [不相容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 資料庫實施使用基於GTID的復寫，例如 [Google Cloud SQL第二代執行個體](https://cloud.google.com/sql/docs/features#differences). 將MySQL for Cloud SQL 8.0作為替代方案。

>[!NOTE]
>
>如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的任務，請參閱 [設定遠程MySQL資料庫連接](mysql-remote.md).

## 在Ubuntu上安裝MySQL

Adobe Commerce和Magento Open Source2.4需要乾淨地安裝MySQL 8.0。請按照以下連結了解在電腦上安裝MySQL的說明。

* [烏邦圖](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您預期要匯入大量產品，您可以 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 大於預設值，16 MB。

>[!NOTE]
>
>預設值會套用至雲端基礎架構上的Adobe Commerce _和_ 內部項目。 Adobe Commerce on cloud infrastructure Pro客戶必須開立支援票證，以增加 `max_allowed_packet` 值。 Adobe Commerce on cloud infrastructure Starter客戶可以更新 `/etc/mysql/mysql.cnf` 檔案。

若要增加值，請開啟 `/etc/mysql/mysql.cnf` 檔案，並找出 `max_allowed_packet`. 將變更儲存至 `mysql.cnf` 檔案，關閉文本編輯器，然後重新啟動MySQL(`service mysql restart`)。

要（可選）驗證您設定的值，請在 `mysql>` 提示：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然後， [配置資料庫實例](#configuring-the-database-instance).

## MySQL 8更改

針對Adobe Commerce和Magento Open Source2.4，我們新增了對MySQL 8的支援。
本節介紹開發人員應注意的MySQL 8的重大更改。

### 移除整數類型的寬度（邊框間距）

MySQL 8.0.17中已棄用整數資料類型(TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT)的顯示寬度規範。在其輸出中包含資料類型定義的語句不再顯示整數類型的顯示寬度，TINYINT(1)除外。 MySQL連接器假設TINYINT(1)列源自於布林值列。 此例外可讓他們繼續作出該假設。

#### 範例

在mysql 8.19上描述admin_user

| 欄位 | 類型 | Null | 金鑰 | 預設 | 額外 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 否 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 是 |  | `NULL` |  |
| `lastname` | `varchar(32`) | 是 |  | `NULL` |  |
| `email` | `varchar(128)` | 是 |  | `NULL` |  |
| `username` | `varchar(40)` | 是 | UNI | `NULL` |  |
| `password` | `varchar(255)` | 否 |  | `NULL` |  |
| `created` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 |  | `NULL` |  |
| `lognum` | `smallint unsigned` | 否 |  | `0` |  |

除 _TINYINT(1)_，應從 `db_schema.xml` 檔案。

如需詳細資訊，請參閱 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 預設順序（按行為）

在8.0之前，條目按外鍵排序。 預設排序順序取決於使用的引擎。
如果您的程式碼依賴特定排序，請一律指定排序順序。

### 已棄用的ASC和DESC限定符（按組）

自MySQL 8.0.13起，已過時 `ASC` 或 `DESC` 限定符 `GROUP BY` 子句已刪除。 以前依賴的查詢 `GROUP BY` 排序可能會產生與以前的MySQL版本不同的結果。 要生成給定的排序順序，請提供 `ORDER BY` 條。

## 商務和MySQL 8

Adobe Commerce和Magento Open Source已進行一些變更，以正確支援MySQL 8。

### 查詢和插入行為

Adobe Commerce和Magento Open Source在 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 禁用驗證後，MySQL可能會截斷資料。 在MySQL中，查詢行為已更改： `Select * on my_table where IP='127.0.0.1'` 不再傳回結果，因為IP位址現在已正確地視為字串，而非整數。

## 從MySQL 5.7升級到MySQL 8

要正確地將MySQL從5.7版更新到8版，必須按照以下步驟操作：

1. 將Adobe Commerce或Magento Open Source升級至2.4.0。測試所有項目，並確定您的系統如預期般運作。
1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 進行資料庫備份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 將MySQL更新為8版。
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

本節探討如何為Adobe Commerce或Magento Open Source建立資料庫例項。 雖然建議使用新的資料庫實例，但您可以選擇安裝Adobe Commerce或使用現有資料庫實例安裝Magento Open Source。

配置MySQL資料庫實例：

1. 以任何用戶身份登錄到資料庫伺服器。
1. 轉到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 提示時的用戶密碼。
1. 按如下順序輸入以下命令，以建立名為 `magento` 使用者名稱 `magento`:

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

1. 輸入 `exit` 退出命令提示符。

1. 驗證資料庫：

   ```bash
   mysql -u magento -p
   ```

   如果顯示MySQL監視器，則已正確建立資料庫。 如果顯示錯誤，請重複前面的命令。

1. 如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的任務，請參閱 [設定遠程MySQL資料庫連接](mysql-remote.md).

   建議您根據業務需要配置資料庫實例。 在配置資料庫時，請記住以下事項：

   * 索引器要求更高 `tmp_table_size` 和 `max_heap_table_size` 值（如64 M）。 如果您設定 `batch_size` 參數時，您可以調整該值以及表大小設定，以改善索引器效能。 請參閱 [最佳化指南](../../../performance/configuration.md) 以取得更多資訊。

   * 為獲得最佳效能，請確保所有MySQL和Adobe Commerce或Magento Open Source索引表都可以保留在記憶體中(例如，配置 `innodb_buffer_pool_size`)。

   * 與其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新編製索引所花的時間更長。 請參閱 [設定最佳實務](../../../performance/configuration.md#indexers).

1. MySQL `TIMESTAMP` 要遵循應用程式聲明性架構（系統變數）所期望的首選項和組成的欄位 `explicit_defaults_for_timestamp` 必須設為 `on`.

   參考：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未啟用此設定， `bin/magento setup:db:status` 總是報告 `Declarative Schema is not up to date`.

>[!NOTE]
>
>此 `explicit_defaults_for_timestamp` 已棄用設定。 此設定控制將在未來的MySQL版本中刪除的已廢止的TIMESTAMP行為。 移除這些行為時， `explicit_defaults_for_timestamp` 也會移除設定。

>[!WARNING]
>
>針對雲端基礎架構專案的Adobe Commerce, `explicit_defaults_for_timestamp` 為MySQL(MariaDB)設定預設為 _關閉_.

與其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新編製索引所花的時間更長。 要加快重新索引，建議設定以下MariaDB配置參數：

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_astiplity = 1
