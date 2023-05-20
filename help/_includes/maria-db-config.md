---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---
# MariaDB配置設定

與以前的MariaDB或MySQL版本相比，在MariaDB 10.4和10.6上重新索引花費的時間更長。 要加快重新索引，建議設定以下MariaDB配置參數：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

如果您在升級到MariaDB 10.6後遇到與索引無關的效能降級，請考慮啟用 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 的子菜單。 比如說， `--query-cache-type=ON`。

除了這些建議之外，您還應與資料庫管理員協商配置以下參數：

>[!NOTE]
>
>這些設定僅可用於內部部署。 Adobe Commerce雲基礎架構上的客戶無權訪問這些設定。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
