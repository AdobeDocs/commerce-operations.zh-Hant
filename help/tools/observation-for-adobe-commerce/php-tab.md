---
title: '[!UICONTROL PHP]索引標籤'
description: 瞭解 [!DNL Observation for Adobe Commerce]的[!UICONTROL PHP]標籤。
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# [!UICONTROL PHP]索引標籤

**PHP**&#x200B;標籤顯示PHP處理問題，以提供對PHP問題的更深入分析。

## [!UICONTROL PHP active process details]

![PHP使用中處理序詳細資料](../../assets/tools/php-active-process-details.jpg)

**[!UICONTROL PHP active process details]**&#x200B;框架顯示所選時間範圍內的PHP程式，包括php-fpm。

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP處理序載入](../../assets/tools/php-process-load.jpg)

**[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]**&#x200B;框架顯示所選時間範圍內來自PHP-FPM程式的CPU負載。

## [!UICONTROL PHP Memory detail]

![PHP記憶體詳細資料](../../assets/tools/php-memory-detail.jpg)

**[!UICONTROL PHP Memory detail]**&#x200B;框架顯示所選時間範圍內PHP處理程式的記憶體使用量。

## [!UICONTROL PHP CPU Utilization]

![PHP CPU使用率](../../assets/tools/php-cpu-utilization.jpg)

**[!UICONTROL PHP CPU Utilization]**&#x200B;框架顯示所選時間範圍內PHP處理作業的CPU使用率。

## [!UICONTROL PHP Process states]

![PHP處理狀態](../../assets/tools/php-process-states-image-1.jpg)

**[!UICONTROL PHP Process states]**&#x200B;框架顯示所選時間範圍內的PHP程式狀態。 當PHP處理序終止和重新啟動時，它就會顯示。 請注意未顯示重新啟動的已終止PHP處理序。

* &#39;%NOTICE：正在終止……%&#39;)為&#39;php_term&#39;
* &#39;%注意：正在結束，再見！%&#39;)作為&#39;php_exit&#39;
* &#39;%注意： fpm正在執行，pid%&#39;)為&#39;fpm_start&#39;
* &#39;%NOTICE：已準備好處理連線%&#39;)為&#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![PHP錯誤](../../assets/tools/php-errors-image-1.jpg)

**[!UICONTROL PHP Errors]**&#x200B;框架顯示所選時間範圍內的PHP Worker錯誤數目。 剖析和顯示的錯誤訊息包括：

* &#39;%worker_connections不足%&#39;)做為&#39;worker&#39;
* &#39;%PHP嚴重錯誤：允許的記憶體大小！%&#39;)，作為&#39;mem_size&#39;
* &#39;%exited on signal 11 (SIGSEGV)%&#39;)為&#39;sig_11&#39;
* &#39;%exited on signal 7 (SIGBUS)%&#39;)為&#39;sig_7&#39;
* &#39;%increase pm.start_servers%&#39;)作為&#39;pmstart_serv&#39;
* &#39;%max_children%&#39;)做為&#39;max_children_cnt&#39;
* &#39;%PHP嚴重錯誤：允許的記憶體大小為%&#39;)為&#39;mem_exhst_coun&#39;
* &#39;%無法為集區%配置記憶體&#39;)做為&#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;)作為&#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;)做為&#39;opc_sv_comments&#39;
* &#39;%PHP嚴重錯誤：未攔截到的RedisException：連線%&#39;上的讀取錯誤)為&#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![個PHP處理序計數](../../assets/tools/php-processes-count.jpg)

**[!UICONTROL PHP processes count]**&#x200B;框架顯示所選時間範圍內的PHP處理序計數。

## [!UICONTROL Database Errors]

![資料庫錯誤](../../assets/tools/php-tab-database-errors.jpg)

**[!UICONTROL Database Errors]**&#x200B;框架顯示所選時間範圍內的資料庫錯誤。 剖析的錯誤包括：

* &#39;%配置給暫存資料表的記憶體大小超過innodb_buffer_pool_size%&#39;的20%)為&#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP： rbr write fail%&#39;)為&#39;rbr_write_fail&#39;
* &#39;%mysqld：磁碟已滿%&#39;)做為&#39;disk_full&#39;
* &#39;%Error number 28%&#39;)作為&#39;err_28&#39;
* &#39;%rollback%&#39;)為&#39;rollback&#39;
* &#39;%資料表%&#39;的外部索引鍵條件約束失敗)為&#39;foreign_key_constraint&#39;
* &#39;%Error_code： 1114%&#39;)做為&#39;sql_1114_full&#39;
* &#39;%CRITICAL： SQLSTATE[HY000] [2006] MySQL伺服器已消失%&#39;)為&#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040]連線數太多%&#39;)為&#39;sql_1040&#39;
* &#39;%CRITICAL： SQLSTATE[HY000] [2002]%&#39;)為&#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]：%&#39;)為&#39;sql_1047&#39;
* &#39;%[警告]已中止連線%&#39;)為&#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]：完整性條件約束違規：%&#39;)為&#39;sql_23000&#39;
* &#39;%1205鎖定等待逾時%&#39;)為&#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049]未知的資料庫%&#39;)為&#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]：找不到基底資料表或檢視：%&#39;)為&#39;sql_42S02&#39;
* &#39;%General error： 1114%&#39;)作為&#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;)為&#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]：找不到資料行： 1054 Unknown column%&#39;)為&#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]：語法錯誤或存取違規：%&#39;)為&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]：基數違規：%&#39;)為&#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]：%&#39;)為&#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000]具有IP位址%的使用者端)為&#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]：一般錯誤： 2014%&#39;)為&#39;sql_2014&#39;
* &#39;%1927連線已終止%&#39;)為&#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB：%&#39;)做為&#39;sql_1062_e&#39;
* &#39;%[注意] WSREP：正在將記憶體對應排清到磁碟……%&#39;)做為&#39;mem_map_flush&#39;
* &#39;%Internal MariaDB錯誤碼： 1146%&#39;)為&#39;sql_1146&#39;
* &#39;%Internal MariaDB錯誤碼： 1062%&#39;)為&#39;sql_1062&#39; * &#39;%1062 [警告] InnoDB：%&#39;)為&#39;sql_1062_w&#39;
* &#39;%Internal MariaDB錯誤碼： 1064%&#39;)為&#39;sql_1064&#39;
* &#39;%InnoDB：檔案中的宣告失敗%&#39;)為&#39;assertion_err&#39;
* &#39;%mysqld_safe目前執行的處理序數目： 0%&#39;)為&#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld取得signal%&#39;)為&#39;mysql_sigterm&#39;
* &#39;%1452 Cannot add%&#39;)為&#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;)做為&#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]：一般錯誤： 3%&#39;)為&#39;cnt_wrt_tmp&#39;
* &#39;%General error： 1 %&#39;)作為&#39;sql_syntax&#39;
* &#39;%42S22%&#39;)做為&#39;sql_42S22&#39;
* &#39;%InnoDB：錯誤（索引鍵重複）%&#39;)，因為&#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![資料庫追蹤](../../assets/tools/php-tab-database-traces.jpg)

**[!UICONTROL Database traces]**&#x200B;框架顯示資料庫追蹤資訊。 此框架會與所選時間軸的APM交易摘要檢視對齊。

## [!UICONTROL Database mysql-slow.log]

![資料庫mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

**[!UICONTROL Database mysql-slow.log]**&#x200B;框架顯示所選時間範圍內`mysql-slow.log`檔案中的查詢陳述式型別。
