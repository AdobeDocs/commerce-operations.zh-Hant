---
title: 「 [!UICONTROL Deploy] 標籤」
description: 了解 [!UICONTROL Deploy] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: b95a35ee64cd8e844a51a9ff699eceb9c3a9266c
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# 此 [!UICONTROL Deploy] 標籤

此頁簽旨在快速隔離部署問題和原因。

## [!UICONTROL Deploy log Deployment Troubleshooter]

![部署日誌部署疑難解答](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

此 **[!UICONTROL Deploy log Deployment Troubleshooter]** frame會顯示在所選時間範圍內發生的部署記錄事件計數。 目的是提供部署活動的概覽，並依計數來判斷部署的複雜性。 記錄越多的訊息，部署通常就越複雜。

## [!UICONTROL Deploy State]

![部署狀態](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

此 **[!UICONTROL Deploy State]** frame會顯示在選取的時間範圍內發生的部署事件。 此幀的解析器正在查找以下特定信號：

* 「%NOTICE:正在開始生成命令%&#39;)，作為&#39;start_gen&#39;
* 「%git apply /app/vendor/magento/ece-tools/patches%」)作為「apply_patches」
* 「%Set標誌：.static_content_deploy%&#39;)作為&#39;SCD&#39;
* 「%NOTICE:生成命令已完成%」)，作為「gen_compl」
* 「%NOTICE:正在開始部署。%&#39;)作為&#39;start_deploy&#39;
* 「%NOTICE:部署完成%」)作為「deploy_compl」
* 「%NOTICE:開始部署後。%&#39;)作為&#39;start_pdeploy&#39;
* 「%NOTICE:後部署完成%」)作為「pdeploy」
* &#39;%deploy-complete%&#39;)作為&#39;cl_deploy_compl&#39;

## [!UICONTROL Deploy Log Detail]

![部署日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

此 **[!UICONTROL Deploy Log Detail]** frame會顯示在所選時間範圍內發生的部署日誌消息摘要詳細資訊。 該幀正在解析部署日誌中的以下字串：

* 「%NOTICE:正在開始部署。%&#39;)作為&#39;start_dply&#39;
* 「%INFO:起始案例：scenario/deploy.xml%&#39;)作為&#39;start_scenario&#39;
* 「%NOTICE:開始預部署%」)作為「strt_predply」
* 「%資訊：正在恢復修補程式日誌檔案%&#39;)，為&#39;rstr_ptch_log&#39;
* 「%INFO:正在更新快取配置。%&#39;)作為&#39;updt_cach_config&#39;
* 「%INFO:將Redis從連接%」設定為「redis_sec_conn_set」
* 「%INFO:在建置掛接期間執行靜態內容部署，清除舊內容%&#39;)，如&#39;scd_build_hk&#39;
* 「%INFO:清除pub/static%」)，作為「clr_pub_static」
* 「%NFO:正在清除REDIS快取：%&#39;)，作為&#39;clr_redis_cach&#39;
* 「%INFO:清除var/cache目錄%&#39;)，作為&#39;clr_var_cach&#39;
* 「%通知：啟用維護模式%」)作為「enable_maint_mode」
* 「%INFO:停用cron%」)作為「disable_cron」
* 「%INFO:嘗試終止正在運行的cron作業，消費者處理%&#39;)為「kill_cron_try」
* 「%INFO:未找到正在運行的Magentocron和用戶進程。%&#39;)作為&#39;no_cron_fnd&#39;,
* %通知：驗證配置%」)為「validate_config」
* 「%在初始安裝期間建立管理員用戶需要以下管理員資料%」)，作為「no_admin」
* 「%建議滿足約束%」的PHP版本)作為「php_ver_constraint」
* 「%警告：將具有指定建議的配置修正為「fix_config_sugg」
* 「%警告： [2003年] 尚未配置錯誤報告的目錄嵌套級別值。%&#39;)as&#39;nest_err_reporting&#39;
* 「%NOTICE:驗證結束%」)作為「end_validation」
* 「%NOTICE:正在啟動更新。%&#39;)作為&#39;start_update&#39;
* 「%INFO:正在更新env.php。%&#39;)作為&#39;update_php_env&#39;
* 「%INFO:正在更新env.php DB連接配置。%&#39;)作為&#39;update_php_env_db&#39;
* 「%INFO:將env.php AMQP配置%&#39;)更新為&#39;update_php_env_amqp&#39;
* 「%INFO:將搜尋引擎設為：elasticsearch7%&#39;)作為&#39;set_elastic7&#39;
* 「%elasticsearch 6.5.4已傳遞EOL%」)作為「elastic_ver_EOL」
* 「%INFO:將搜尋引擎設為：elasticsearch6%&#39;)作為&#39;set_elastic6&#39;
* 「%INFO:將安全和不安全的URL%」更新為「update_urls」
* 「%INFO:正在運行安裝程式升級。%&#39;)作為&#39;setup_upgrade_run&#39;
* 「%INFO:已啟用部署後掛接。 Cron啟用、快取清除和預警操作將延遲%」)，為「post_hook_enabled」
* 「%NOTICE:已禁用維護模式。%&#39;)作為&#39;maint_mode_disabled
* 「%INFO:情節(s)已完成%」)作為「scenario_finished」
* 「%警告：命令維護：enable已完成，但出現錯誤。 建立維護標誌檔案%&#39;)，為&#39;enable_maintenance_fail&#39;
* 「%MySQL Server已消失%」)，作為「MySQL_has_gone_away」

## [!UICONTROL Post Deploy Log Detail]

![部署後日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

此 **[!UICONTROL Post Deploy Log Detail]** frame會顯示在所選時間範圍內發生的部署後記錄詳細資訊。 此幀的焦點是包含以下字串的特定日誌消息：

* &#39;%Disabled maintenance mode%&#39;)，作為&#39;disabled_maint_mode&#39;
* 「%INFO:起始案例：scenario/post-deploy.xml%&#39;)作為&#39;start_pstdply_scenario&quot;
* 「%通知：驗證配置%」)為「val_config」
* 「%通知：驗證%」)作為「end_val_config」
* 「%INFO:啟用cron%&#39;)為&#39;cron_enabled&#39;
* 「%資訊：建立重要檔案的備份。%&#39;)作為&#39;file_backup&#39;
* 「%INFO:已成功建立備份%」)作為「file_backup_success」
* 「%INFO:開始頁面升溫%&#39;)為&#39;pg_warmup_start&#39;
* 「%INFO:熱化頁面：%&#39;)作為「womned_up_pg」
* 「%ERROR:升溫失敗：%&#39;)為「warm_up_pg_err」
* 「%資訊：情節(s)已完成%」)作為「scenario_finished」

## [!UICONTROL Cloud Log Detail]

![雲日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

此 **[!UICONTROL Cloud Log Detail]** frame會顯示在所選時間範圍內發生的雲記錄詳細資訊。 以下字串會以下方的&#39;AS&#39;標籤剖析並傳回：

* 「%DEBUG:/bin/bash -c &quot;set -o pipefail;php 。/bin/magento setup:upgrade%&#39;)作為&#39;start_update&#39;
* 「%架構建立/更新：%」)作為「schema_updates」
* 「%無要導入的內容。%&#39;)作為&#39;mod_import_finish&#39;
* 「%NOTICE:更新結束。%&#39;)作為&#39;update_finished&#39;
* 「%DEBUG:執行步驟：deploy-static-content%&#39;)作為&#39;scd_run&#39;
* 「%通知：正在跳過靜態內容部署。 SCD隨選啟用。%&#39;)作為&#39;scd_ondemand&#39;
* 「%INFO:清除%&#39;)為&#39;clr_dirs&#39;
* 「%DEBUG:步驟「deploy-static-content」finished%」)作為「scd_finished」
* 「%NOTICE:正在跳過靜態內容壓縮。 SCD隨選啟用。%&#39;)作為&#39;scd_compression_run&#39;,
* 「%INFO:清除var/cache目錄%&#39;)，作為&#39;clr_var_cach&#39;
* 「%DEBUG:步驟「compress-static-content」finished%」)作為「scd_compression_finished」
* 「%DEBUG:執行步驟：deploy-complete%&#39;)作為&#39;deploy_finished&#39;
* 「%INFO:已啟用部署後掛接。 Cron啟用、快取清除和預熱操作會延遲至部署後階段。%&#39;)作為&#39;Post_deploy_hook_enabled&#39;
* 「%NOTICE:已禁用維護模式。%&#39;)作為&#39;maint_mode_disabled
* 「%INFO:情節(s)已完成%」)作為「scenario_finished」
* &#39;%post-deploy.xml%&#39;)作為&#39;post_deploy_start&#39;
* 「%NOTICE:驗證配置%」)為「validate_config」
* 「%警告： [2003年] 尚未配置錯誤報告的目錄嵌套級別值。%&#39;)as&#39;nest_err_reporting&#39;
* 「%NOTICE:驗證結束%」)作為「end_validation」
* 「%INFO:啟用cron%」)作為「enable_cron」
* 「%INFO:建立重要檔案%&#39;的備份)，作為&#39;create_backup&#39;
* 「%DEBUG:步驟「backup」已完成%」)作為「backup_finished」
* 「%INFO:開始頁面升溫%」)為「warmup_start」
* 「%ERROR:升溫失敗：%&#39;)為「warm_up_fail」
* 「%DEBUG:將「熱暖」完成%」步驟為「warmup_finished」
* 「%調試：步驟「時間到第一個位元組」已完成%」)，作為「ttfb_finished」
* 「%INFO:情節(s)已完成%」)為「post_deploy_finished」
* 「%DEBUG:執行步驟：pre-build%&#39;)作為&#39;run_pre-build&#39;
* 「%DEBUG:將.static_content_deploy已被刪除%&#39;)標籤為「scd_flag_del」
* 「%DEBUG:步驟「pre-build」finished%」)，作為「pre-build_completed」
* 「%NOTICE:應用修補程式%」)作為「apply_patches」
* 「%已應用%」)作為「patches_applied」
* 「%DEBUG:步驟「apply-patches」已完成%」)作為「apply_patches_complete」
* 「%使用快速策略%」進行部署)為「quick_strategy_deploy」
* 「%通知：運行ID編譯%」)作為「di_compliation_start」
* 「%NOTICE:運行ID編譯%」的結束)，作為「di_compliation_finished」
* 「%NOTICE:正在生成新靜態內容%」)，作為「gen_frsh_static_content」
* &#39;%magento安裝程式:static-content:deploy%&#39;)作為&#39;scd_executing&#39;
* 「%NOTICE:結束生成新靜態內容%」)，作為「gen_frsh_static_cont_finished」
* 「%INFO:起始案例：scenario/build/transfer.xml%&#39;)作為&#39;start_transferxml&quot;
* 「%INFO:嘗試終止運行cron作業%」)作為「kill_crons」
* 「%INFO:正在清除密文快取：%&#39;)，作為&#39;clear_redis_cache&#39;
* 「%INFO:檢查db是否存在，並將%&#39;)作為&#39;db_check&#39;
* 「%警告： [2010年] Elasticsearch服務安裝在基礎架構層，但不用作搜索引擎。%&#39;)as&#39;es_not_used_used
* 「%NOTICE:正在啟動更新。%&#39;)作為&#39;starting_update&#39;
* 「%INFO:將搜尋引擎設為：mysql%&#39;)作為&#39;mysql_search&#39;
* &#39;%SQLSTATE[HY000] [2006年] MySQL Server已消失%&#39;)，為「mysql_gone」

## [!UICONTROL Count of modules imported during deploy]

![部署期間導入的模組數](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

此 **[!UICONTROL Count of modules imported during deploy]** frame會顯示在所選時間範圍內部署期間匯入的模組數。

## [!UICONTROL Deployed module list]

![已部署的模組清單](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

此 **[!UICONTROL Deployed module list]** 框架顯示在所選時間範圍內部署的模組。

