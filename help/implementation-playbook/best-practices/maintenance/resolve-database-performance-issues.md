---
title: 解決資料庫效能問題的最佳實務
description: 瞭解如何修正雲端基礎結構上部署的Adobe Commerce網站上效能緩慢的資料庫問題。
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# 解決資料庫效能問題的最佳實務

本文討論如何修正雲端基礎結構網站上Adobe Commerce上資料庫效能受到負面影響的資料庫問題。

## 受影響的版本

Adobe Systems Commerce on 雲端基礎結構

## 識別和解析長時間運行的查詢

確定您是否有任何運行緩慢的MySQL查詢。 根據您的Adobe Systems商務雲端基礎結構計劃以及工具的可用性，您可以執行以下操作。

### 使用 MySQL 分析資料庫查詢

您可以使用 MySQL 來識別和解析任何Adobe Systems Commerce on 雲端基礎結構 專案上長時間運行的查詢。

1. 執行[`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html)陳述式。
1. 如果您發現長時間執行查詢，請針對每個查詢執行[MySQL `EXPLAIN`和`EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/)，找出造成查詢長時間執行的原因。
1. 根據發現的問題，採取措施修正查詢，使其更快地執行。

### 使用Percona Toolkit分析查詢（僅適用於Pro架構）

如果您的Adobe Commerce專案部署在Pro架構上，您可以使用Percona Toolkit來分析查詢。

1. 對MySQL慢速查詢記錄檔執行`pt-query-digest --type=slowlog`命令。
   * 要查找慢速查詢日誌的位置，請參閱 **[!UICONTROL Log locations > Service Logs]**&#x200B;開發人員文檔中的 （https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs）。
   * [請參閱 Percona 工具包 > pt-查詢-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 文檔。
1. 根據發現的問題，採取措施修復查詢，使其運行得更快。

## 驗證所有表是否都具有主鍵

定義主鍵是良好的資料庫和表設計的必要條件。 主鍵提供了一種唯一標識任何表中單個行的方法。

如果您的表格沒有主索引鍵，則Adobe Commerce (InnoDB)的預設資料庫引擎會使用第一個唯一的非null索引鍵作為主索引鍵。 如果沒有可用的唯一索引鍵，InnoDB會建立隱藏的主索引鍵（6位元組）。 隱含定義的主索引鍵問題是您無法控制它。 此外，隱含值會全域指派給沒有主索引鍵的所有表格。 如果您同時在這些資料表上執行寫入，此組態可能會造成爭用問題。 這可能會導致效能問題，因為表格也共用全域隱藏的主要索引鍵索引增量。

針對任何沒有主索引鍵的表格定義主索引鍵，以防止出現這些問題。

### 識別並更新沒有主索引鍵的表格

1. 使用以下 SQL 查詢標識沒有主鍵的表：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 對於缺少主鍵的任何表，請使用類似於以下內容的節點更新 `db_schema.xml` （聲明性綱要） 來添加主鍵：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   新增節點時，請將 和 `column name` 變數取代`referenceID`為自定義自定義值。

有關詳細資訊，請參閱 [開發人員文檔中的配置聲明性綱要](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 。

## 識別和刪除重複索引

識別資料庫中的任何重複索引並將其移除。

### 檢查重複的索引

若要檢查Pro或Starter雲端架構上的重複索引，請執行下列SQL查詢。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查詢會傳回資料行名稱和任何重複索引的名稱。

Pro架構商戶也可以使用Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)`指令來執行檢查。

### 移除重複的索引

使用 SQL [刪除索引語句](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 刪除重複索引。

```SQL
DROP INDEX
```

## 其他資訊

[雲端部署的資料庫配置最佳實踐](../planning/database-on-cloud.md)
