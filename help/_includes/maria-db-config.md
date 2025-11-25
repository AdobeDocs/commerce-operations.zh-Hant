---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB組態設定

與舊版MariaDB或MySQL相比，在MariaDB 10.4和10.6上重新索引需要更多時間。 若要加速重新索引，建議您設定這些MariaDB設定引數：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

如果您在升級至MariaDB 10.6後遇到與索引無關的效能降低，請考慮啟用[`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type)設定。 例如，`--query-cache-type=ON`。

在雲端基礎結構專案上升級Adobe Commerce之前，您可能還需要升級MariaDB （[請參閱MariaDB升級最佳實務](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)）。

例如：

* Adobe Commerce 2.4.6含MariaDB 10.5.1版或更新版本
* Adobe Commerce 2.3.5含MariaDB 10.3版或更舊版本

除了這些建議之外，您應該洽詢資料庫管理員設定下列引數：

>[!NOTE]
>
>這些設定僅適用於內部部署。 雲端基礎結構上的Adobe Commerce客戶無權存取這些設定。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
