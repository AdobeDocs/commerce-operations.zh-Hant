---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---
# MariaDB配置設定

與以前的MariaDB或MySQL版本相比，在MariaDB 10.4和10.6上重新編製索引所花的時間更長。 要加快重新索引，建議設定以下MariaDB配置參數：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

如果您在升級到MariaDB 10.6後遇到與索引化無關的效能降低，請考慮啟用 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 設定。 例如， `--query-cache-type=ON`.

除了這些建議外，您還應就下列參數的設定與資料庫管理員協商：

>[!NOTE]
>
>這些設定僅適用於內部部署。 雲端基礎架構上的Adobe Commerce客戶無法存取這些設定。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
