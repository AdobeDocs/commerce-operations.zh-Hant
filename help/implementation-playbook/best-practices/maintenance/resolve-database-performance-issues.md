---
title: 解決資料庫效能問題的最佳實務
description: 了解如何修正部署在雲端基礎架構上的Adobe Commerce網站上，導致效能下降的資料庫問題。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


<!--Consider moving this topic to the Maintenance section-->

# 解決資料庫效能問題的最佳實務

本文探討如何修正對雲端基礎架構網站上的Adobe Commerce資料庫效能造成負面影響的資料庫問題。

## 受影響的版本

Adobe Commerce雲基礎架構

## 識別並解析長時間運行的查詢

確定是否運行MySQL查詢時速度較慢。 根據您的Adobe Commerce雲端基礎架構計畫，以及因此工具的可用性，您可以執行下列操作。

### 使用MySQL分析資料庫查詢

您可以使用MySQL來識別和解決雲基礎架構專案上任何Adobe Commerce的長時間執行查詢。

1. 執行 [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 語句。
1. 如果您看到長時間運行的查詢，請運行 [MySQL `EXPLAIN` 和 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 找出讓查詢長時間執行的原因。
1. 根據發現的問題，採取步驟修正查詢，使其更快速地執行。

### 使用Percona Toolkit（僅適用於Pro架構）分析查詢

如果您的Adobe Commerce專案部署在Pro架構上，則可使用Percona Toolkit分析查詢。

1. 執行 `pt-query-digest --type=slowlog` 命令。
   * 若要尋找查詢記錄緩慢的位置，請參閱 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs)。
   * 請參閱 [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 檔案。
1. 根據發現的問題，採取步驟修正查詢，使其更快速地執行。

## 驗證所有表都具有主鍵

定義主鍵是良好的資料庫和表設計的要求。 主鍵提供了唯一標識任何表中單個行的方法。

如果您的表沒有主鍵，則Adobe Commerce(InnoDB)的預設資料庫引擎將第一個唯一非空鍵用作主鍵。 如果沒有可用的唯一鍵，InnoDB將建立隱藏的主鍵（6個位元組）。 隱式定義主鍵的問題在於您無法控制它。 此外，對於沒有主鍵的所有表，都全局分配隱式值。 如果對這些表執行同時寫入，此配置可能會導致爭用問題。 這可能會導致效能問題，因為表也共用全局隱藏主鍵索引增量。

通過為任何沒有主鍵的表定義主鍵來防止這些問題。

### 標識和更新沒有主鍵的表

1. 使用以下SQL查詢標識沒有主鍵的表：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 對於缺少主鍵的任何表，請通過更新 `db_schema.xml` （聲明性架構），其節點類似下列：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   新增節點時，請取代 `referenceID` 和 `column name` 變數與自訂值。

如需詳細資訊，請參閱 [配置聲明性架構](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 在開發人員檔案中。

## 標識和刪除重複索引

在資料庫中標識任何重複索引並刪除它們。

### 檢查重複索引

要在Pro或Starter雲架構上檢查重複索引，請運行以下SQL查詢。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查詢返回列名和任何重複索引的名稱。

專業體系結構的商家也可以使用Percona Toolkit運行檢查  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 命令。

### 刪除重複索引

使用SQL [DROP INDEX語句](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 刪除重複索引。

```SQL
DROP INDEX
```

## 其他資訊

[雲端部署的資料庫設定最佳實務](../planning/database-on-cloud.md)

