---
title: 資料庫復寫
description: 瞭解設定資料庫復寫的優點。
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 資料庫復寫

{{ee-only}}

{{deprecate-split-db}}

設定資料庫復寫可提供下列優點：

- 提供資料備份
- 啟用資料分析，而不影響主資料庫
- 擴充性

MySQL資料庫會以非同步方式復寫，這表示從屬端不需要永久連線，即可接收主端的更新。

## 設定資料庫復寫

有關資料庫復寫的深入討論不在本指南的討論範圍內。 若要進行設定，您可以諮詢資源，例如：

- [MySQL檔案](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [如何在MySQL (digitalocean)中設定主從式復寫](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce提供從屬資料庫的MySQL設定範例。 提供簡單組態與`ResourceConnections`類別`README.md`。

下列為更進階的內容，僅供您參考：

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## 效能提升

若要改善主從式複製的效能，您可以篩選從執行處理上的某些表格。 我們建議篩選用於目錄搜尋且名稱模式為`search\_tmp\_%`的所有暫存表格。

若要這麼做，請在您的從屬執行個體上的`my.cnf`檔案中新增下列行：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
