---
title: 「 [!UICONTROL PHP] 標籤」
description: 了解 [!UICONTROL PHP] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: 28055eb09235912c66c637990e2081a70e1c7808
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# 此 [!UICONTROL PHP] 標籤

此 **PHP** 頁簽顯示PHP進程問題，以便對PHP問題進行更深入的分析。

## [!UICONTROL PHP active process details]

![PHP活動進程詳細資訊](../../assets/tools/php-active-process-details.jpg)

此 **[!UICONTROL PHP active process details]** frame顯示所選時間範圍內的PHP進程，包括php-fpm。

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP進程負載](../../assets/tools/php-process-load.jpg)

此 **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** frame顯示所選時間範圍內來自PHP-FPM進程的CPU負載。

## [!UICONTROL PHP Memory detail]

![PHP記憶體詳細資訊](../../assets/tools/php-memory-detail.jpg)

此 **[!UICONTROL PHP Memory detail]** frame顯示PHP進程在選定時間範圍內的記憶體使用情況。

## [!UICONTROL PHP CPU Utilization]

![PHP CPU利用率](../../assets/tools/php-cpu-utilization.jpg)

此 **[!UICONTROL PHP CPU Utilization]** frame顯示PHP進程在選定時間範圍內的CPU百分比利用率。

## [!UICONTROL PHP Process states]

![PHP進程狀態](../../assets/tools/php-process-states-image-1.jpg)

此 **[!UICONTROL PHP Process states]** frame顯示所選時間範圍內的PHP進程狀態。 它顯示在PHP進程終止和重新啟動時。 請注意不顯示重新啟動的已終止PHP進程。

* 「%NOTICE:正在終止……%&#39;)作為&#39;php_term&#39;
* 「%通知：退出，再見！%&#39;)作為&#39;php_exit&#39;
* 「%通知：fpm正在運行，pid%&#39;)為&#39;fpm_start&#39;
* 「%NOTICE:準備處理連接%&#39;)作為「php_ready」

## [!UICONTROL PHP Errors]

![PHP錯誤](../../assets/tools/php-errors-image-1.jpg)

此 **[!UICONTROL PHP Errors]** frame顯示所選時間範圍內PHP工作器錯誤的數量。 剖析並顯示的錯誤訊息包括：

* 「%worker_connections不足%」)作為「worker」
* 「%PHP致命錯誤：允許的記憶體大小！%&#39;)作為&#39;mem_size&#39;
* 「%退出信號11(SIGSEGV)%」)為「sig_11」
* 「%退出信號7(SIGBUS)%」)為「sig_7」
* 「%increase pm.start_servers%」)作為「pmstart_serv」
* 「%max_children%」)作為「max_children_cnt」
* 「%PHP致命錯誤：允許的記憶體大小為%」)，作為「mem_exhst_coun」
* 「%無法為池%」分配記憶體)作為「opc_mem_count」
* 「%警告中間字串緩衝區溢出%」)作為「opc_str_buf」
* 「%非法字串offsetl%」)作為「opc_sv_comments」
* 「%PHP致命錯誤：未捕獲的RedisException:讀取連接%&#39;上的錯誤)作為「php_exc」

## [!UICONTROL PHP processes count]

![PHP進程計數](../../assets/tools/php-processes-count.jpg)

此 **[!UICONTROL PHP processes count]** frame顯示在所選時間範圍內PHP進程的計數。

## [!UICONTROL Database Errors]

![資料庫錯誤](../../assets/tools/php-tab-database-errors.jpg)

此 **[!UICONTROL Database Errors]** frame會顯示所選時間範圍內的資料庫錯誤。 剖析的錯誤包括：

* 「%為臨時表分配的記憶體大小超過innodb_buffer_pool_size%」的20%)，作為「temp_tbl_buff_pool」
* 「%\[ERROR\] WSREP:rbr write fail%&#39;)作為&#39;rbr_write_fail&#39;
* &#39;%mysqld:磁碟已滿%」)作為「disk_full」
* 「%錯誤號28%」)作為「err_28」
* &#39;%rollback%&#39;)作為&#39;rollback&#39;
* &#39;%外鍵約束對表%&#39;失敗)為&#39;foreign_key_constraint&#39;
* 「%錯誤代碼：1114%」)作為「sql_1114_full」
* 「%關鍵：SQLSTATE[HY000] [2006年] MySQL Server已消失%&#39;)，為「sql_gone」
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
* &#39;%SQLSTATE[42000]:語法錯誤或訪問違規：%&#39;)作為&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]:基數違規：%&#39;)作為&#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;)作為&#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] 具有IP地址%&#39;的客戶端)作為&#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]:一般錯誤：2014%」)作為「sql_2014」
* 「%1927連接已終止%」)，為「sql_1927」
* 「%1062 \[ERROR\] InnoDB:%」)作為「sql_1062_e」
* &#39;%[附註] WSREP:正在刷新記憶體映射到磁碟……%&#39;)作為&#39;mem_map_flush&#39;
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
* 「%InnoDB:錯誤（重複密鑰）%&#39;)為&#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![資料庫跟蹤](../../assets/tools/php-tab-database-traces.jpg)

此 **[!UICONTROL Database traces]** frame顯示資料庫跟蹤資訊。 此框架與所選時間軸的APM事務摘要視圖對齊。

## [!UICONTROL Database mysql-slow.log]

![資料庫mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

此 **[!UICONTROL Database mysql-slow.log]** frame會顯示 `mysql-slow.log` 檔案的時間範圍。
