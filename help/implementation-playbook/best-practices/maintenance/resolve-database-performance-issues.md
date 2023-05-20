---
title: 解決資料庫效能問題的最佳做法
description: 瞭解如何解決在雲基礎架構上部署的Adobe Commerce站點上降低效能的資料庫問題。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# 解決資料庫效能問題的最佳做法

本文討論如何修復對雲基礎架構站點上的Adobe Commerce資料庫效能產生負面影響的資料庫問題。

## 受影響的版本

Adobe Commerce在雲基礎架構上

## 確定並解決長時間運行的查詢

確定是否運行MySQL查詢速度較慢。 根據您的Adobe Commerce雲基礎架構規劃以及工具可用性，您可以執行以下操作。

### 使用MySQL分析資料庫查詢

您可以使用MySQL來識別和解決任何Adobe Commerce雲基礎架構項目上長時間運行的查詢。

1. 運行 [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 的雙曲餘切值。
1. 如果您看到長時間運行的查詢，請運行 [MySQL `EXPLAIN` 和 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 查找使查詢長時間運行的原因。
1. 根據發現的問題，採取步驟修複查詢，使其運行更快。

### 使用Percona Toolkit分析查詢（僅適用於Pro體系結構）

如果您的Adobe Commerce項目部署在Pro體系結構上，則可以使用Percona工具包來分析查詢。

1. 運行 `pt-query-digest --type=slowlog` 命令。
   * 要查找慢速查詢日誌的位置，請參見 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs)。
   * 查看 [Percona工具包> pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 文檔。
1. 根據發現的問題，採取步驟修複查詢，使其運行更快。

## 驗證所有表都具有主鍵

定義主鍵是良好資料庫和表設計的要求。 主鍵提供了唯一標識任何表中單行的方法。

如果有沒有主鍵的表，則Adobe Commerce(InnoDB)的預設資料庫引擎將第一個唯一的非空鍵用作主鍵。 如果沒有唯一鍵可用，InnoDB將建立隱藏的主鍵（6位元組）。 隱式定義的主鍵的問題在於您沒有控制它。 此外，為所有沒有主鍵的表全局分配隱式值。 如果對這些表同時執行寫入操作，此配置可能會導致爭用問題。 這可能會導致效能問題，因為表還共用全局隱藏主鍵索引增量。

通過為任何沒有主鍵的表定義主鍵來防止這些問題。

### 標識和更新沒有主鍵的表

1. 使用以下SQL查詢標識沒有主鍵的表：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 對於任何缺少主鍵的表，請通過更新 `db_schema.xml` （聲明性架構），其節點與下列內容類似：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   添加節點時，替換 `referenceID` 和 `column name` 自定義值的變數。

有關詳細資訊，請參見 [配置聲明性架構](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 我們的開發人員文檔中。

## 標識並刪除重複索引

確定資料庫中的任何重複索引並刪除它們。

### 檢查重複索引

要檢查Pro或Starter雲體系結構上的重複索引，請運行以下SQL查詢。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查詢返回任何重複索引的列名和名稱。

專業建築商也可以使用Percona工具包運行檢查  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 的子菜單。

### 刪除重複索引

使用SQL [DROP INDEX語句](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 刪除重複索引。

```SQL
DROP INDEX
```

## 其他資訊

[用於雲部署的資料庫配置最佳做法](../planning/database-on-cloud.md)
