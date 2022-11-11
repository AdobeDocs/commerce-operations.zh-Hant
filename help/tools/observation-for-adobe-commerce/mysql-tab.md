---
title: 「 [!UICONTROL MySQL] 標籤」
description: 了解 [!UICONTROL MySQL] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 8c9753fe5b9038978859cc101d53f897267ecfe9
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 0%

---

# 此 [!UICONTROL MySQL] 標籤

## [!UICONTROL MySQL% free storage by node]

![按節點列出的MySQL%空閒儲存](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

許多問題是由MySQL在分配給MySQL的儲存中的儲存耗盡(`datadir` MySQL配置設定，預設為 `/data/mysql`)或 `tmpdir` 太空了。 預設 `tmpdir` （MySQL設定）為 `/tmp`. 此 **[!UICONTROL MySQL% free storage by node]** 框看 `/, /tmp` （如果定義為獨立裝載）和 `/data/mysql` 可用儲存的百分比。 從MySQL 5.7版（MariaDB 10.2版）開始，未壓縮 `tmp` 表被寫入 `tmp` 表空間 `/data/mysql` 檔案(ibtmp1)中的目錄。 預設情況下，此檔案會自動展開而無限制。 由於它是表空間，因此它不會減小大小，並且在MySQL重新啟動時將重置為12MB。

## [!UICONTROL MySQL Connections by Node]

![按節點列出的MySQL連接](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

此 **[!UICONTROL MySQL Connections by Node]** frame表示資料庫節點中斷或連接量大的週期。

## [!UICONTROL MySQL Node Summary]

![MySQL節點摘要](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

此 **[!UICONTROL MySQL Node Summary]** 表顯示了資料庫節點詳細資訊，如軟體版本和實例類型（大小）。

## [!UICONTROL Galera Number of Nodes in cluster]

![群集中的加萊拉節點數](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

此 **[!UICONTROL Galera Number of Nodes in cluster]** 框架顯示來自MySQL日誌的資訊。 當節點加入並離開叢集時，只會顯示所選時間範圍的訊息。 如果節點在該時間範圍之前離開群集，則在該時間範圍內將不存在任何消息。 如果您懷疑資料庫可能運行不足節點，請將時間範圍擴展到較長的時段，以查看您是否可以看到其他資訊。 如果時段內的資訊表示少於 [!DNL Galera] 群集，請展開時間範圍，查看是否可以確定節點何時離開叢集。

## [!UICONTROL MySQL shutdowns and starts]

![MySQL關閉和啟動](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

此 **[!UICONTROL MySQL shutdowns and starts]** frame會檢測節點何時關閉。 此 [!DNL Galera] 節點將被逐出，並自行從 [!DNL Galera] 節點。 這通常會導致重新啟動MySQL服務。

## [!UICONTROL Galera log]

![加萊拉日誌](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

此 **[!UICONTROL Galera log]** frame顯示MySQL日誌中有關 [!DNL Galera] 節點、其狀態，以及 [!DNL Galera] 群集。

* 「%1047 WSREP尚未準備用於應用程式的節點%」)作為「node_not_prep_for_use」
* 「%\[ERROR\] WSREP:無法讀取：wsrep_sst_xtrabackup-v2%&#39;)作為&#39;xtrabackup_read_fail&#39;
* 「%\[ERROR\] WSREP:已完成進程，但出現錯誤：wsrep_sst_xtrabackup-v2 %&#39;)作為&#39;xtrabackup_compl_w_err&#39;
* 「%\[ERROR\] WSREP:rbr write fail%&#39;)作為&#39;rbr_write_fail&#39;
* 「%selfleave%」)作為「susp_node」
* 「%members = 3/3（已加入/總計）%」)作為「3of3」
* 「%members = 2/3（已加入/總計）%」)作為「2of3」
* 「%members = 2/2%」)作為「2of2」
* 「%members = 1/2%」)作為「1of2」
* 「%members = 1/3%」)作為「1of3」
* 「%members = 1/1%」)作為「1of1」
* 「%\[注意\] /usr/sbin/mysqld(mysqld 10)。%&#39;)as&#39;sql_restart&#39;
* 「%仲裁：沒有狀態為「%」的節點)作為「no_node_count」
* 「%WSREP:成員0%」)作為「mem_0」
* 「%WSREP:成員1.0%」)作為「mem_1」
* 「%WSREP:成員2%&#39;)作為&#39;mem2&#39;
* 「%WSREP:與組同步，已準備好連接%&#39;)，為「就緒」
* 「%/usr/sbin/mysqld，版本：%」)作為「mysql_restart_mysql.slow」
* 「%\[注意\] WSREP:新群集視圖：全局狀態：%&#39;)作為&#39;galera_cluster_view_chng&#39;

## [!UICONTROL Galera Log by Host]

![按主機列出的加萊拉日誌](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

此 **[!UICONTROL Galera Log by Host]** 框架與 **[!UICONTROL Galera log]** 框架，但會依節點劃分，以協助疑難排解。

## [!UICONTROL Database performance]

![資料庫效能](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

此 **[!UICONTROL Database performance]** frame顯示特定請求期間的資料庫效能。 您可以按一下圖形下方彩色圖示中的每個量度，以查看這些量度。 許多量度 [使用新Relic監視MySQL資料庫效能](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) 在此框架中找到。

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![事務資料庫調用計數](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

此 **[!UICONTROL Transaction Database Call Count]** frame顯示每個事務方面進行的資料庫調用數。 這似乎是以行為中心，而不是陳述。

## [!UICONTROL Cron_schedule table updates]

![Cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

此 **[!UICONTROL Cron_schedule table updates]** frame顯示所選時段內對cron_schedule表進行資料庫更新的最大持續時間。

## [!UICONTROL Slow Query Traces]

![查詢跟蹤速度慢](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

此 **[!UICONTROL Slow Query Traces]** frame會顯示查詢追蹤緩慢的表格和請求類型。 會為超過5秒的查詢事務建立慢速查詢跟蹤。 此框架的重要之處在於更新查詢。 如果表格由 `UPDATE`, `DELETE`，和 `INSERT` 語句，它們可以鎖定表一段時間。

平均 `SELECT` 如果與FOR UPDATE一起使用，語句可以鎖定行。

## [!UICONTROL Datastore Operations tables]

![資料儲存操作表](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Cron表格變更](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

此 **[!UICONTROL Cron table change]** frame查找「無法獲取cron作業的鎖：」錯誤消息，以及涉及特定PHP記憶體錯誤和鎖 `cron_schedule` 表格。 若 `cron_schedule` 表格已鎖定(例如， `DELETE` 查詢)，則會封鎖其他cron。

## [!UICONTROL Deadlocks]

![死鎖](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

此 **[!UICONTROL Deadlocks]** frame會查看從MySQL日誌中剖析的以下字串：

* 「%PHP致命錯誤：允許的記憶體大小為%&#39;)，作為php_mem_error
* &#39;%get鎖定；嘗試重新啟動事務，查詢：DELETE自\&#39;cron_schedule%&#39;)為cron_sched_lock_del
* 「%鎖定cron作業：indexer_reindex_all_invalid%&#39;)作為&#39;lock_indexer_reindex_all_invalid%&#39;
* 「%鎖定cron作業：cron_schedule%」)作為「lock_cron_schedule」
* 「%鎖定cron作業：%」)為「total_cron_lock」
* 「%常規錯誤：1205鎖等待超時超出%」)作為「sql_1205_lock」
* 「%ERROR 1213(40001):嘗試獲取lock%」時發現死鎖)為「sql_1213_lock」
* &#39;%SQLSTATE[40001]:序列化失敗：1213已找到死鎖%」)，作為「sql_1213_lock2」
* 「%鎖定cron作業：indexer_update_all_views%&#39;)作為「lock_indexer_update_all_views」
* 「%鎖定cron作業：sales_grid_order_invoice_async_insert%&#39;)作為「lock_sales_grid_order_invoice_async_insert」，
* 「%鎖定cron作業：staging_remove_updates%&#39;)作為&#39;lock_staging_remove_updates&#39;
* 「%鎖定cron作業：sales_grid_order_shipment_async_insert%&#39;)作為「lock_sales_grid_order_shipment_async_insert」
* 「%鎖定cron作業：amazon_payments_process_queued_requeds%&#39;)作為&#39;lock_amazon_payments_process_queueds_revids&#39;
* 「%鎖定cron作業：sales_send_order_shimpting_emails%&#39;)作為&#39;lock_sales_send_order_shimpt_emails&#39;
* 「%鎖定cron作業：staging_synchronize_entities_period%&#39;)作為&#39;lock_staging_synchronize_entities_period&#39;
* 「%鎖定cron作業：indexer_clean_all_changelogs%&#39;)作為「lock_indexer_clean_all_changelogs」
* 「%鎖定cron作業：magento_targetrule_index_reindex%&#39;)為&#39;lock_magento_targetrule_index_reindex&#39;
* 「%鎖定cron作業：newsletter_send_all%」)作為「lock_newsletter_send_all」
* 「%鎖定cron作業：newsletter_send_all%」)作為「lock_newsletter_send_all」
* 「%鎖定cron作業：sales_send_order_emails%&#39;)作為&#39;lock_sales_send_order_emails&#39;
* 「%鎖定cron作業：sales_send_order_creditmemo_emails%&#39;)作為&#39;lock_sales_send_order_creditmemo_emails&#39;
* 「%鎖定cron作業：sales_grid_order_creditmemo_async_insert%&#39;)作為&#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* 「%鎖定cron作業：bulk_cleanup%&#39;)作為&#39;lock_bulk_cleanup&#39;
* 「%鎖定cron作業：flush_preview_quotas%&#39;)作為&#39;lock_flush_preview_quotas&#39;
* 「%鎖定cron作業：sales_send_order_invoice_emails%&#39;)作為&#39;lock_sales_send_order_invoice_emails&#39;
* 「%鎖定cron作業：sales_send_order_invoice_emails%&#39;)作為&#39;lock_sales_send_order_invoice_emails&#39;
* 「%鎖定cron作業：captcha_delete_expired_images%&#39;)作為「lock_captcha_delete_expired_images」
* 「%鎖定cron作業：magento_newrelicreporting_cron%&#39;)作為&#39;lock_magento_newrelicreporting_cron&#39;
* 「%鎖定cron作業：actoped_authentication_failures_cleanup%」)作為「lock_optaded_authentication_failures_cleanup」
* 「%鎖定cron作業：send_notification%&#39;)作為&#39;lock_send_notification&#39;
* 「%鎖定cron作業：magento_giftcardaccount_generage_codes_pool%&#39;)作為&#39;lock_magento_giftcardaccount_generage_codes_pool&#39;
* 「%鎖定cron作業：catalog_product_frontend_actions_flush%」)作為「lock_catalog_product_frontend_actions_flush」
* 「%鎖定cron作業：mysqlmq_clean_messages%&#39;)作為&#39;mysqlmq_clean_messages&#39;
* 「%鎖定cron作業：catalog_product_attribute_value_synchronize%&#39;)作為&#39;lock_catalog_product_attribute_value_synchronize&#39;
* 「%鎖定cron作業：ddg_automation_importer%&#39;)作為&#39;lock_ddg_automation_importer&#39;
* 「%鎖定cron作業：ddg_automation_reviews_and_wishlist%&#39;)作為&#39;lock_ddg_automation_reviews_and_wishlist&#39;
* 「%鎖定cron作業：captcha_delete_old_attempts%」)作為「lock_captcha_delete_old_attmets」
* 「%鎖定cron作業：catalog_product_opdate_price_values_cleanup%」)作為「lock_catalog_product_opdate_price_values_cleanup」
* 「%鎖定cron作業：consumers_runner%&#39;)作為&#39;lock_condusers_runner&#39;
* 「%鎖定cron作業：ddg_automation_customer_guester_sync%&#39;)作為&#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* 「%鎖定cron作業：get_amazon_capture_updates%」)作為「lock_get_amazon_capture_updates」
* 「%鎖定cron作業：get_amazon_authorization_updates%&#39;)作為&#39;lock_send_get_amazon_authorization_updates&#39;
* 「%鎖定cron作業：temando_process_platform_events%&#39;)作為&#39;lock_temando_process_platform_events&#39;
* 「%鎖定cron作業：ddg_automation_status%&#39;)作為&#39;lock_ddg_automation_status&#39;
* 「%鎖定cron作業：ddg_automation_status%&#39;)作為&#39;lock_ddg_automation_status&#39;
* 「%鎖定cron作業：sales_clean_orders%&#39;)作為&#39;lock_sales_clean_orders&#39;
* 「%鎖定cron作業：catalog_index_refresh_price%」)作為「lock_catalog_index_refresh_price」
* 「%鎖定cron作業：magento_reward_balance_warning_notification%」)，作為「lock_magento_reward_balance_warning_notification」
* 「%鎖定cron作業：analytics_update%」)作為「lock_analytics_update」
* 「%鎖定cron作業：messagequeue_clean_oquadtid_locks%&#39;)作為&#39;lock_messageue_clean_ocquated_locks&#39;
* 「%鎖定cron作業：messagequeue_clean_oquadtid_locks%&#39;)作為&#39;lock_messageue_clean_ocquated_locks&#39;
* 「%鎖定cron作業：staging_apply_version%」)作為「lock_staging_apply_version」
* 「%鎖定cron作業：magento_reward_expire_points%」)作為「lock_magento_reward_expire_points」
* 「%鎖定cron作業：yotpo_yotpo_orders_sync%&#39;)作為&#39;lock_yotpo_yotpo_orders_sync&#39;
* 「%鎖定cron作業：catalog_event_status_checker%&#39;)作為&#39;lock_catalog_event_status_checker&#39;
* 「%鎖定cron作業：ddg_automation_campaign%」)作為「lock_ddg_automation_campaign」
* 「%鎖定cron作業：visitor_clean%&#39;)作為&#39;lock_visitor_clean&#39;
* 「%鎖定cron作業：scconnector_verify_website%」)作為「lock_scconnector_verify_website」
* 「%鎖定cron作業：ddg_automation_email_templates%&#39;)作為&#39;lock_ddg_automation_email_templates&#39;
* 「%鎖定cron作業：aggregate_sales_report_order_data%&#39;)作為&#39;lock_aggregate_sales_report_order_data&#39;
* 「%鎖定cron作業：ddg_automation_catalog_sync%&#39;)作為&#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![資料庫統計資訊](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

此 **[!UICONTROL DB Statistics]** frame每秒顯示刪除、寫入、讀取、更新和慢速查詢。

## [!UICONTROL Request frequency]

![要求頻率](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![資料庫錯誤](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

此 **[!UICONTROL Database Errors]** 框架顯示各種資料庫 [警告和錯誤](https://mariadb.com/kb/en/mariadb-error-codes/):

* 「%為臨時表分配的記憶體大小超過innodb_buffer_pool_size%」的20%，作為「temp_tbl_buff_pool」
* 「%\[ERROR\] WSREP:rbr write fail%&#39;)作為&#39;rbr_write_fail&#39;
* &#39;%mysqld:磁碟已滿%」)作為「disk_full」
* 「%錯誤號28%」)作為「err_28」
* &#39;%rollback%&#39;)作為&#39;rollback&#39;
* &#39;%外鍵約束對表%&#39;失敗)為&#39;foreign_key_constraint&#39;
* 「%錯誤代碼：1114%」)作為&#39;sql_1114_full&quot;%CRITICAL:SQLSTATE[HY000] [2006年] MySQL Server已消失%&#39;)，為「sql_gone」
* &#39;%SQLSTATE[HY000] [1040] 太多連接%」)作為「sql_1040」
* 「%關鍵：SQLSTATE[HY000] [2002年]%&#39;)作為&#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;)作為&#39;sql_1047&#39;
* &#39;%[警告] 已中止連接%」)作為「aborted_conn」
* &#39;%SQLSTATE[23000]:完整性約束衝突：%&#39;)作為&#39;sql_23000&#39;
* 「%1205鎖定等待超時%」)作為「sql_1205」
* &#39;%SQLSTATE[HY000] [1049] 未知資料庫%&#39;)作為&#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]:找不到基表或視圖：%&#39;)作為「sql_42S02」
* 「%常規錯誤：1114%」)作為「sql_1114」
* &#39;%SQLSTATE[40001]%&#39;)作為&#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]:未找到列：1054未知欄%」)作為「sq1_1054」
* &#39;%SQLSTATE[42000]:語法錯誤或訪問違規：%&#39;)as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]:基數違規：%&#39;)作為&#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;)作為&#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] 具有IP地址%&#39;的客戶端)作為&#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]:一般錯誤：2014%」)作為「sql_2014」
* 「%1927連接已終止%」)，為「sql_1927」
* 「%1062 \[ERROR\] InnoDB:%」)作為「sql_1062_e」
* &quot;%&quot;[附註] WSREP:正在刷新記憶體映射到磁碟……%&#39;)作為&#39;mem_map_flush&#39;
* 「%內部MariaDB錯誤代碼：1146%」)作為「sql_1146」
* 「%內部MariaDB錯誤代碼：1062%」)作為「sql_1062」*「%1062 [警告] InnoDB:%&#39;)作為&#39;sql_1062_w&#39;
* 「%內部MariaDB錯誤代碼：1064%」)作為「sql_1064」
* 「%InnoDB:檔案%中的斷言失敗」)作為「assertion_err」
* 「%mysqld_safe當前正在運行的進程數：0%&#39;)作為&#39;mysql_oom&#39;
* 「%\[錯誤\] mysqld got signal%」)作為「mysql_sigterm」
* 「%1452無法添加%」)為「sql_1452」
* 「%ERROR 1698%」)作為「sql_1698」
* &#39;%SQLSTATE[HY000]:一般錯誤：3%&#39;)作為&#39;cnt_wrt_tmp
* 「%常規錯誤：1 %&#39;)作為&#39;sql_syntax
* 「%42S22%」)作為「sql_42S22」
* 「%InnoDB:錯誤（重複密鑰）%&#39;)作為「innodb_dup_key」從日誌時間序列

## [!UICONTROL DB Error Table]

![資料庫錯誤表](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

此 **[!UICONTROL DB Error Table]** 框架顯示與 **[!UICONTROL Database Errors]** 框架，但您可以依節點和表格格式查看。 請參閱 [MariaDB錯誤代碼](https://mariadb.com/kb/en/mariadb-error-codes/) 以取得更多資訊。

## [!UICONTROL Database Traces]

![資料庫跟蹤](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

此 **[!UICONTROL Database Traces]** frame按類型顯示選定時間軸上的資料庫跟蹤。

## [!UICONTROL Database processes]

![資料庫進程](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

此 **[!UICONTROL Database processes]** frame顯示資料庫進程、環境和節點標識符。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![按節點列出的MySQL非休眠線程](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

此 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame顯示與資料庫的連接線程。 此幀顯示活動線程。

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL按環境運行和休眠線程](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

此 **[!UICONTROL MySQL Running and Sleeping Threads by environment]** frame顯示與資料庫的活動連接和休眠連接。 如果與慢速查詢已進入休眠狀態的資料庫有連接，則會有休眠連接。 休眠連接可以是被鎖定行或表阻止的資料庫查詢。 這些休眠連接還保留PHP工作器連接。

## [!UICONTROL MySQL mem used by node]

![節點使用的MySQL記憶體](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

此 **[!UICONTROL MySQL mem used by node]** frame按MySQL顯示記憶體的節點使用情況。 在較大的站點上，此幀可能是連續的長條，使用的記憶體值為GB。

## [!UICONTROL Database mysql-slow.log]

![資料庫mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

此 **[!UICONTROL Database mysql-slow.log]** frame會顯示 `mysql-slow.log` 檔案的時間範圍。

