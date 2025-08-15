---
title: MariaDB的Adobe Commerce升級必要條件
description: 瞭解如何準備Adobe Commerce資料庫，以從舊版升級MariaDB。
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# 升級MariaDB的必要條件

在雲端基礎結構上升級Adobe Commerce之前，如果您使用MariaDB，可能還需要升級資料庫軟體。 例如：

- Adobe Commerce 2.4.6含MariaDB 10.5.1版或更新版本
- Adobe Commerce 2.3.5含MariaDB 10.3版或更舊版本

## Adobe Commerce 2.4.6

從MariaDB 10.5.1開始，在`/* mariadb-5.3 */`、`SHOW CREATE TABLE`、`SHOW COLUMNS`陳述式的輸出以及`DESCRIBE`表格的`COLUMN_TYPE`資料行中，使用舊暫時格式的資料行標示為`INFORMATION_SCHEMA.COLUMNS`註解。 [請參閱MariaDB檔案](https://mariadb.com/kb/en/datetime/#internal-format)。

由於MariaDB註解，Adobe Commerce無法將日期欄對應到適當的資料型別，這可能會導致自訂程式碼中出現無法預期的行為。

為避免將MariaDB從舊版升級至10.6版時出現意外行為，Adobe建議將欄移轉至新的內部格式。

### 預設設定

在MariaDB 10.1.2中，從MySQL 5.6引進了新的暫時格式。`mysql56_temporal_format`系統變數可讓資料庫在執行變更表格或匯入資料庫時，自動將舊日期格式轉換為新日期格式。 雲端基礎結構上的Adobe Commerce一律會啟用`mysql56_temporal_format`的預設設定。

### 移轉日期欄

下列查詢顯示將MariaDB升級至10.5.1或更新版本後，必須移轉的受影響表格和欄：

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

將欄移轉至新的內部日期格式需要重新匯入資料庫，或使用相同的欄定義在已識別的欄上執行變更。 下列查詢會產生必要的變更查詢：

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>在部署新程式碼之前&#x200B;_，請務必將資料行移轉至新的內部日期格式_，以避免非預期的行為。

## Adobe Commerce 2.3.5

將雲端基礎結構上的MariaDB服務從版本10.0或10.2升級至版本10.3、10.4或10.5。MariaDB版本10.3和更新版本會要求資料庫使用動態表格列格式，而Adobe Commerce會要求表格使用InnoDB儲存引擎。 本文會說明如何更新資料庫以符合這些MariaDB要求。

準備資料庫後，請先提交Adobe Commerce支援票證以更新雲端基礎結構上的MariaDB服務版本，然後再繼續進行Adobe Commerce升級程式。

### 準備資料庫以進行升級

在Adobe Commerce支援團隊開始升級程式之前，請先轉換資料庫表格以準備資料庫：

- 將資料列格式從`COMPACT`轉換為`DYNAMIC`
- 將儲存引擎從`MyISAM`變更為`InnoDB`

計畫和排程轉換時，請謹記下列考量事項：

- 在大型資料庫中，從`COMPACT`轉換為`DYNAMIC`資料表可能需要數小時的時間。

- 若要防止資料損毀，請勿在已上線的網站上完成轉換工作。

- 在網站上的低流量期間完成轉換工作。

- 在執行轉換資料庫表格的命令之前，請將網站切換為[維護模式](../../../installation/tutorials/maintenance-mode.md)。

#### 轉換資料庫表格列格式

您可以轉換叢集中一個節點上的表格。 變更會自動復寫到其他服務節點。

1. 在雲端基礎結構環境中，從您的Adobe Commerce使用SSH連線至節點1。

1. 登入MariaDB。

1. 識別要從壓縮格式轉換為動態格式的表格。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 決定表格大小，以便排程轉換工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   較大的表格需要較長時間才能轉換。 複查表格並按優先順序和表格大小批次轉換工作，以協助規劃所需的維護視窗。

1. 將所有表格一次轉換一個動態格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### 轉換資料庫表格儲存體格式

您可以轉換叢集中一個節點上的表格。 變更會自動復寫到其他服務節點。

Adobe Commerce Starter和Adobe Commerce Pro專案的儲存格式轉換程式不同。

- 對於入門架構，請使用MySQL `ALTER`命令來轉換格式。
- 在Pro架構上，使用MySQL `CREATE`和`SELECT`命令建立具有`InnoDB`儲存體的資料庫表格，並將資料從現有表格複製到新表格中。 此方法可確保將變更復寫到叢集中的所有節點。

**轉換Adobe Commerce Pro專案的資料表儲存格式**

1. 識別使用`MyISAM`儲存空間的資料表。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 將所有資料表一次轉換成`InnoDB`儲存格式。

   - 重新命名現有表格以避免名稱衝突。

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - 使用現有資料表的資料，建立使用`InnoDB`儲存空間的資料表。

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - 確認新表格具有所有必要的資料。

   - 刪除您重新命名的原始表格。


**轉換Adobe Commerce Starter專案的資料表儲存格式**

1. 識別使用`MyISAM`儲存空間的資料表。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 將使用`MyISAM`儲存空間的資料表轉換為`InnoDB`儲存空間。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### 驗證資料庫轉換

在排程升級至MariaDB 10.3、10.4或10.6版的前一天，請確認所有表格都具有正確的列格式和儲存引擎。 需要進行驗證，因為完成轉換後進行的程式碼部署可能會導致某些表格恢復為原始設定。

1. 登入您的資料庫。

1. 檢查是否有任何資料表仍採用`COMPACT`資料列格式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 檢查是否有任何資料表仍使用`MyISAM`儲存格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果有任何表格已還原，請重複這些步驟以變更表格列格式和儲存引擎。

### 變更儲存引擎

請參閱[將MyISAM資料表轉換為InnoDB](../planning/database-on-cloud.md)。
