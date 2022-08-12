---
title: 「 [!UICONTROL Deploy] 頁籤
description: 瞭解 [!UICONTROL Deploy] 頁籤 [!DNL Observation for Adobe Commerce]。
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# 的 [!UICONTROL Deploy] 頁籤

此頁籤嘗試快速隔離問題和部署問題的原因。

## [!UICONTROL Deploy log Deployment Troubleshooter]

![部署日誌部署疑難解答](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

的 **[!UICONTROL Deploy log Deployment Troubleshooter]** frame顯示在選定時間範圍內發生的部署日誌事件的計數。 目的是提供部署活動的一覽式視圖，並根據計數確定部署的複雜性。 消息記錄越多，部署通常就越複雜。

## [!UICONTROL Deploy State]

![部署狀態](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

的 **[!UICONTROL Deploy State]** frame顯示在選定時間範圍內發生的部署事件。 此幀的分析器正在查找以下特定信號：

* 「%NOTICE:正在啟動generate命令%&#39;)，作為「start_gen」
* 「%git apply /app/vendor/magento/ece-tools/patches%」)作為「apply_patches」
* 「%Set標誌：.static_content_deploy%&#39;)作為「SCD」
* 「%NOTICE:生成命令completed%」)作為「gen_compl」
* 「%NOTICE:正在開始部署。%&#39;)作為「start_deploy」
* 「%NOTICE:部署已完成%」)作為「deploy_compl」
* 「%NOTICE:正在啟動部署後。%&#39;)作為「start_pdeploy」
* 「%NOTICE:部署後完成%)作為「pdeploy」
* 「%deploy-complete%」)作為「cl_deploy_compl

## [!UICONTROL Deploy Log Detail]

![部署日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

的 **[!UICONTROL Deploy Log Detail]** frame顯示在選定時間範圍內發生的部署日誌消息摘要詳細資訊。 幀正在分析部署日誌中的以下字串：

* 「%NOTICE:正在開始部署。%&#39;)作為「start_dply」
* 「%INFO:開始方案：scenario/deploy.xml%&#39;)作為&#39;start_scenario
* 「%NOTICE:正在啟動pre-deploy%&#39;)，作為「strt_predply」
* 「%資訊：正在將修補程式日誌檔案%&#39;)還原為「rstr_ptch_log」
* 「%INFO:正在更新快取配置。%&#39;)作為「updt_cach_config」
* 「%INFO:將Redis從連接%&#39;設定為&#39;redis_sec_conn_set&#39;
* 「%INFO:在生成掛接期間執行靜態內容部署，清除舊內容%&#39;)，如「scd_build_hk」
* 「%INFO:正在將pub/static%」)作為「clr_pub_static」
* 「%NFO:正在將redis快取：%&#39;)清除為&#39;clr_redis_cach&#39;
* 「%INFO:清除var/cache目錄%&#39;)為「clr_var_cach」
* 「%通知：啟用維護模式%」)為「enable_maint_mode」
* 「%INFO:禁用cron%」)為「disable_cron」
* 「%INFO:嘗試終止正在運行的cron作業，使用者將進程%」)作為「kill_cron_try」
* 「%INFO:找不到正在運行Magentocron和使用者進程。%&#39;)作為「no_cron_fnd」，
* %NOTICE:正在驗證配置%&#39;)為「validate_config」
* 「%初始安裝期間建立管理員用戶需要以下管理資料%」)，作為「no_admin」
* 「%recommended PHP version seffed the constraint%」（滿足約束%）作為「php_ver_constraint」
* 「%警告：使用給定建議將配置修復為「fix_config_sug」
* 「%警告： [2003] 尚未配置錯誤報告的目錄嵌套級別值。%&#39;)作為nest_err_reporting&#39;
* 「%NOTICE:驗證%」的結束)作為「end_validation」
* 「%NOTICE:正在啟動更新。%&#39;)作為「start_update」
* 「%INFO:正在更新env.php。%&#39;)作為「update_php_env」
* 「%INFO:正在更新env.php DB連接配置。%&#39;)作為「update_php_env_db」
* 「%INFO:正在將env.php AMQP配置%&#39;)更新為&#39;update_php_env_amqp&#39;
* 「%INFO:將搜索引擎設定為：elasticsearch7%」)作為「set elastic7」
* 「%elasticsearch 6.5.4已通過EOL%」)，作為「elastic_ver_EOL」
* 「%INFO:將搜索引擎設定為：elasticsearch6%」)作為「set elastic6」
* 「%INFO:正在將安全和不安全的URL%」更新為「update_urls」
* 「%INFO:正在運行安裝程式升級。%&#39;)作為「setup_upgrade_run」
* 「%INFO:已啟用部署後掛接。 Cron啟用、快取清理和預警告操作被推遲%」)，作為「post_hook_enabled」
* 「%NOTICE:已禁用維護模式。%&#39;)作為「maint_mode_disabled」
* 「%INFO:已完成%」)作為「scenario_finished」
* 「%警告：命令維護：啟用已完成，但出現錯誤。 將maintenanceflag file%&#39;)建立為&#39;enable_maintenance_fail&#39;
* 「%MySQL Server已離開%」)，作為「MySQL_has_gone_away」

## [!UICONTROL Post Deploy Log Detail]

![發佈部署日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

的 **[!UICONTROL Post Deploy Log Detail]** frame顯示在選定時間範圍內發生的部署後日誌詳細資訊。 此框架側重於包含以下字串的特定日誌消息：

* 「%Disabled maintenance mode%」)作為「disabled_maint_mode」
* 「%INFO:開始方案：scenario/post-deploy.xml%&#39;)作為&#39;start_pstdply_scenario
* 「%通知：正在驗證配置%&#39;)為「val_config」
* 「%通知：驗證%」的結束)，作為「end_val_config」
* 「%INFO:啟用cron%&#39;)作為「cron_enabled」
* 「%資訊：建立重要檔案的備份。%&#39;)作為「file_backup」
* 「%INFO:已成功將備份%&#39;)建立為「file_backup_success」
* 「%INFO:正在啟動頁面預熱%&#39;)，為&quot;pg_warmup_start&quot;
* 「%INFO:已熱化頁面：%&#39;)，為&quot;bernet_up_pg&quot;
* 「%錯誤：預熱失敗：%&#39;)作為「warm_up_pg_err」
* 「%資訊：已完成%」)作為「scenario_finished」

## [!UICONTROL Cloud Log Detail]

![雲日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

的 **[!UICONTROL Cloud Log Detail]** frame顯示在選定時間範圍內發生的雲日誌詳細資訊。 以下字串將用下面的「AS」標籤進行分析並返回：

* 「%DEBUG:/bin/bash -c &quot;設定 — o管道失效；php。/bin/magento setup:upgrade%&#39;)作為「start_update」
* 「%架構建立/更新：%」)作為「schema_updates」
* 「%沒有要導入的內容。%&#39;)作為「mod_import_finish」
* 「%NOTICE:更新結束。%&#39;)作為「update_finished」
* 「%DEBUG:運行步驟：deploy-static-content%」)作為「scd_run」
* 「%通知：正在跳過靜態內容部署。 SCD按需啟用。%&#39;)作為「scd_ondemand」
* 「%INFO:正在清除%&#39;)作為&#39;clr_dirs&#39;
* 「%DEBUG:步驟「deploy-static-content」 finished%」)作為「scd_finished」
* 「%NOTICE:正在跳過靜態內容壓縮。 SCD按需啟用。%&#39;)作為「scd_compression_run」，
* 「%INFO:清除var/cache目錄%&#39;)為「clr_var_cach」
* 「%DEBUG:步驟&quot;compress-static-content&quot; finished%&quot;)作為「scd_compression_finished」
* 「%DEBUG:運行步驟：deploy_complete%」)作為「deploy_finished」
* 「%INFO:已啟用部署後掛接。 Cron啟用、快取清理和預預熱操作被推遲到部署後階段。%&#39;)作為「Post_deploy_hook_enabled」
* 「%NOTICE:已禁用維護模式。%&#39;)作為「maint_mode_disabled」
* 「%INFO:已完成%」)作為「scenario_finished」
* 「%post-deploy.xml%」)作為「post_deploy_start」
* 「%NOTICE:正在驗證配置%&#39;)為「validate_config」
* 「%警告： [2003] 尚未配置錯誤報告的目錄嵌套級別值。%&#39;)作為nest_err_reporting&#39;
* 「%NOTICE:驗證%」的結束)作為「end_validation」
* 「%INFO:啟用cron%」)作為「enable_cron」
* 「%INFO:建立重要檔案%&#39;的備份)作為「create_backup」
* 「%DEBUG:步驟「備份」已完成%」)作為「backup_finished」
* 「%INFO:正在啟動頁面預熱%」)，作為「warmup_start」
* 「%錯誤：預熱失敗：%&#39;)作為「warm_up_fail」
* 「%DEBUG:步驟「預熱」完成%」)為「warmup_finished」
* 「%調試：步驟「時間到第一位元組」完成%」)作為「ttfb_finished」
* 「%INFO:方案完成%」)為「post_deploy_finished」
* 「%DEBUG:運行步驟：預生成%」)作為「run_pre-build」
* 「%DEBUG:已將.static_content_deploy標籤為「scd_flag_del」
* 「%DEBUG:步驟「預生成」完成%」)作為「預生成_已完成」
* 「%NOTICE:正在將修補程式%&#39;)作為「apply_patches」
* 「%已應用%」)作為「patches_applied」
* 「%DEBUG:步驟&quot;apply-patches&quot;已完成%&quot;)作為&quot;apply_patches_complete&quot;
* 「%Deploy using quick strategy%」)作為「quick_strategy_deploy」
* 「%通知：正在運行DI編譯%&#39;)作為「di_compliation_start」
* 「%NOTICE:將DI編譯%&#39;運行為&#39;di_compliation_finished&#39;
* 「%NOTICE:正在生成新靜態內容%&#39;)，作為&quot;gen_frsh_static_content&quot;
* &#39;%magento安裝程式:static-content:deploy%&#39;)作為「scd_executing」
* 「%NOTICE:生成新靜態內容%&#39;的結束)，作為&quot;gen_frsh_static_cont_finished&quot;
* 「%INFO:開始方案：scenario/build/transfer.xml%&#39;)作為&#39;start_transferxml
* 「%INFO:正在嘗試將運行的cronjobs%」作為「kill_crons」
* 「%INFO:正在將redis快取：%&#39;)清除為&quot;clear_redis_cache&quot;
* 「%INFO:檢查db是否存在和hastables%&#39;)作為「db_check」
* 「%警告： [2010] Elasticsearch服務安裝在基礎架構層，但不用作搜索引擎。%&#39;)作為&#39;es_not_used&#39;
* 「%NOTICE:正在啟動更新。%&#39;)作為「starting_update」
* 「%INFO:將搜索引擎設定為：mysql%&#39;)作為「mysql_search」
* 「%SQLSTATE」[HY000] [2006] MySQL Server已離開%」)，作為「mysql_gone」

## [!UICONTROL Count of modules imported during deploy]

![部署期間導入的模組計數](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

的 **[!UICONTROL Count of modules imported during deploy]** frame顯示在選定時間範圍內部署期間導入的模組數。

## [!UICONTROL Deployed module list]

![已部署模組清單](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

的 **[!UICONTROL Deployed module list]** frame顯示在選定時間範圍內部署的模組。

