---
title: 資料庫複製
description: 請參閱配置資料庫複製的優點。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# 資料庫複製

{{ee-only}}

{{deprecate-split-db}}

設定資料庫複製可提供下列優點：

- 提供資料備份
- 啟用資料分析，而不影響主資料庫
- 可擴充性

MySQL資料庫非同步複製，這意味著從伺服器不需要永久連接以接收主伺服器的更新。

## 配置資料庫複製

有關資料庫複製的深入討論不在本指南的討論範圍內。 若要設定，您可以查詢資源，例如：

- [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [如何在MySQL(digitalocean)中設定主從複製](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

商務提供從資料庫的MySQL配置示例。 提供簡單的設定， `ResourceConnections` 類 `README.md`.

下列項目更進階，僅供您參考：

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

## 效能改善

要提高主從複製的效能，可以篩選從實例上的一些表。 建議篩選所有具有名稱模式的臨時表 `search\_tmp\_%` 用於目錄搜尋。

若要這麼做，請將下列行新增至 `my.cnf` 檔案：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
