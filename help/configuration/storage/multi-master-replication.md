---
title: 資料庫複製
description: 請參見配置資料庫複製的好處。
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# 資料庫複製

{{ee-only}}

{{deprecate-split-db}}

設定資料庫複製具有以下優點：

- 提供資料備份
- 啟用資料分析而不影響主資料庫
- 可擴充性

MySQL資料庫非同步複製，這意味著從屬資料庫不需要永久連接來從主資料庫接收更新。

## 配置資料庫複製

對資料庫複製的深入討論超出本指南的範圍。 要設定它，您可以咨詢資源，如：

- [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [如何在MySQL中設定主從複製(digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce為從資料庫提供MySQL配置示例。 提供一種簡單的配置 `ResourceConnections` 類 `README.md`。

以下更高級，僅供您參考：

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

## 效能改進

為了提高主從複製的效能，可以過濾從實例上的某些表。 我們建議過濾所有具有名稱模式的臨時表 `search\_tmp\_%` 用於 [目錄](https://glossary.magento.com/catalog) 搜索。

為此，請將以下行添加到 `my.cnf` 從實例上的檔案：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
