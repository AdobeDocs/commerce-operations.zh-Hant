---
title: 的 [!UICONTROL Deploy] 頁籤
description: 瞭解 [!UICONTROL Deploy] 頁籤 [!DNL Observation for Adobe Commerce]。
exl-id: 3e33f7b0-7a40-4598-ae2e-436118e8d99a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
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

* &quot;`%NOTICE: Starting generate command%`&#39;作為&#39;`start_gen`&quot;
* &quot;`%git apply /app/vendor/magento/ece-tools/patches%`&#39;作為&#39;`apply_patches`&quot;
* &quot;`%Set flag: .static_content_deploy%`&#39;作為&#39;`SCD`&quot;
* &quot;`%NOTICE: Generate command completed%`&#39;作為&#39;`gen_compl`&quot;
* &quot;`%NOTICE: Starting deploy.%`&#39;作為&#39;`start_deploy`&quot;
* &quot;`%NOTICE: Deployment completed%`&#39;作為&#39;`deploy_compl`&quot;
* &quot;`%NOTICE: Starting post-deploy.%`&#39;作為&#39;`start_pdeploy`&quot;
* &quot;`%NOTICE: Post-deploy is complete%`&#39;作為&#39;`pdeploy`&quot;
* &quot;`%deploy-complete%`&#39;作為&#39;`cl_deploy_compl`&quot;

## [!UICONTROL Deploy Log Detail]

![部署日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

的 **[!UICONTROL Deploy Log Detail]** frame顯示在選定時間範圍內發生的部署日誌消息摘要詳細資訊。 幀正在分析部署日誌中的以下字串：

* &quot;`%NOTICE: Starting deploy.%`&#39;作為&#39;`start_dply`&quot;
* &quot;`%INFO: Starting scenario(s): scenario/deploy.xml%`&#39;作為&#39;`start_scenario`&quot;
* &quot;`%NOTICE: Starting pre-deploy%`&#39;作為&#39;`strt_predply`&quot;
* &quot;`%INFO: Restoring patch log file%`&#39;作為&#39;`rstr_ptch_log`&quot;
* &quot;`%INFO: Updating cache configuration.%`&#39;作為&#39;`updt_cach_config`&quot;
* &quot;`%INFO: Set Redis slave connection%`&#39;作為&#39;`redis_sec_conn_set`&quot;
* &quot;`%INFO: Static content deployment was performed during build hook, cleaning old content%`&#39;作為&#39;`scd_build_hk`&quot;
* &quot;`%INFO: Clearing pub/static%`&#39;作為&#39;`clr_pub_static`&quot;
* &quot;`%NFO: Clearing redis cache:%`&#39;作為&#39;`clr_redis_cach`&quot;
* &quot;`%INFO: Clearing var/cache directory%`&#39;作為&#39;`clr_var_cach`&quot;
* &quot;`%NOTICE: Enabling Maintenance mode%`&#39;作為&#39;`enable_maint_mode`&quot;
* &quot;`%INFO: Disable cron%`&#39;作為&#39;`disable_cron`&quot;
* &quot;`%INFO: Trying to kill running cron jobs and consumers processes%`&#39;作為&#39;`kill_cron_try`&quot;
* &quot;`%INFO: Running Adobe Commerce cron and consumers processes were not found.%`&#39;作為&#39;`no_cron_fnd`&quot;
* &quot;`%NOTICE: Validating configuration%`&#39;作為&#39;`validate_config`&quot;
* &quot;`%The following admin data is required to create an admin user during initial installation%`&#39;作為&#39;`no_admin`&quot;
* &quot;`%recommended PHP version satisfying the constraint%`&#39;作為&#39;`php_ver_constraint`&quot;
* &quot;`%WARNING: Fix configuration with given suggestions:%`&#39;作為&#39;`fix_config_sugg`&quot;
* &quot;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;作為&#39;`nest_err_reporting`&quot;
* &quot;`%NOTICE: End of validation%`&#39;作為&#39;`end_validation`&quot;
* &quot;`%NOTICE: Starting update.%`&#39;作為&#39;`start_update`&quot;
* &quot;`%INFO: Updating env.php.%`&#39;作為&#39;`update_php_env`&quot;
* &quot;`%INFO: Updating env.php DB connection configuration.%`&#39;作為&#39;`update_php_env_db`&quot;
* &quot;`%INFO: Updating env.php AMQP configuration%`&#39;作為&#39;`update_php_env_amqp`&quot;
* &quot;`%INFO: Set search engine to: elasticsearch7%`&#39;作為&#39;`set_elastic7`&quot;
* &quot;`%elasticsearch 6.5.4 has passed EOL%`&#39;作為&#39;`elastic_ver_EOL`&quot;
* &quot;`%INFO: Set search engine to: elasticsearch6%`&#39;作為&#39;`set_elastic6`&quot;
* &quot;`%INFO: Updating secure and unsecure URLs%`&#39;作為&#39;`update_urls`&quot;
* &quot;`%INFO: Running setup upgrade.%`&#39;作為&#39;`setup_upgrade_run`&quot;
* &quot;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed%`&#39;作為&#39;`post_hook_enabled`&quot;
* &quot;`%NOTICE: Maintenance mode is disabled.%`&#39;作為&#39;`maint_mode_disabled`&quot;
* &quot;`%INFO: Scenario(s) finished%`&#39;作為&#39;`scenario_finished`&quot;
* &quot;`%WARNING: Command maintenance:enable finished with an error. Creating a maintenance flag file%`&#39;作為&#39;`enable_maintenance_fail`&quot;
* &quot;`%MySQL server has gone away%`&#39;作為&#39;`MySQL_has_gone_away`&quot;

## [!UICONTROL Post Deploy Log Detail]

![發佈部署日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

的 **[!UICONTROL Post Deploy Log Detail]** frame顯示在選定時間範圍內發生的部署後日誌詳細資訊。 此框架側重於包含以下字串的特定日誌消息：

* &quot;`%Disabled maintenance mode%`&#39;作為&#39;`disabled_maint_mode`&quot;
* &quot;`%INFO: Starting scenario(s): scenario/post-deploy.xml%`&#39;作為&#39;`start_pstdply_scenario`&quot;
* &quot;`%NOTICE: Validating configuration%`&#39;作為&#39;`val_config`&quot;
* &quot;`%NOTICE: End of validation%`&#39;作為&#39;`end_val_config`&quot;
* &quot;`%INFO: Enable cron%`&#39;作為&#39;`cron_enabled`&quot;
* &quot;`%INFO: Create backup of important files.%`&#39;作為&#39;`file_backup`&quot;
* &quot;`%INFO: Successfully created backup%`&#39;作為&#39;`file_backup_success`&quot;
* &quot;`%INFO: Starting page warming up%`&#39;作為&#39;`pg_warmup_start`&quot;
* &quot;`%INFO: Warmed up page:%`&#39;作為&#39;`warmed_up_pg`&quot;
* &quot;`%ERROR: Warming up failed:%`&#39;作為&#39;`warm_up_pg_err`&quot;
* &quot;`%INFO: Scenario(s) finished%`&#39;作為&#39;`scenario_finished`&quot;

## [!UICONTROL Cloud Log Detail]

![雲日誌詳細資訊](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

的 **[!UICONTROL Cloud Log Detail]** frame顯示在選定時間範圍內發生的雲日誌詳細資訊。 以下字串將用下面的「AS」標籤進行分析並返回：

* &quot;`%DEBUG: /bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade%`&#39;作為&#39;`start_update`&quot;
* &quot;`%Schema creation/updates:%`&#39;作為&#39;`schema_updates`&quot;
* &quot;`%Nothing to import.%`&#39;作為&#39;`mod_import_finish`&quot;
* &quot;`%NOTICE: End of update.%`&#39;作為&#39;`update_finished`&quot;
* &quot;`%DEBUG: Running step: deploy-static-content%`&#39;作為&#39;`scd_run`&quot;
* &quot;`%NOTICE: Skipping static content deploy. SCD on demand is enabled.%`&#39;作為&#39;`scd_ondemand`&quot;
* &quot;`%INFO: Clearing%`&#39;作為&#39;`clr_dirs`&quot;
* &quot;`%DEBUG: Step "deploy-static-content" finished%`&#39;作為&#39;`scd_finished`&quot;
* &quot;`%NOTICE: Skipping static content compression. SCD on demand is enabled.%`&#39;作為&#39;`scd_compression_run`&quot;
* &quot;`%INFO: Clearing var/cache directory%`&#39;作為&#39;`clr_var_cach`&quot;
* &quot;`%DEBUG: Step "compress-static-content" finished%`&#39;作為&#39;`scd_compression_finished`&quot;
* &quot;`%DEBUG: Running step: deploy-complete%`&#39;作為&#39;`deploy_finished`&quot;
* &quot;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed to post-deploy stage.%`&#39;作為&#39;`Post_deploy_hook_enabled`&quot;
* &quot;`%NOTICE: Maintenance mode is disabled.%`&#39;作為&#39;`maint_mode_disabled`&quot;
* &quot;`%INFO: Scenario(s) finished%`&#39;作為&#39;`scenario_finished`&quot;
* &quot;`%post-deploy.xml%`&#39;作為&#39;`post_deploy_start`&quot;
* &quot;`%NOTICE: Validating configuration%`&#39;作為&#39;`validate_config`&quot;
* &quot;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;作為&#39;`nest_err_reporting`&quot;
* &quot;`%NOTICE: End of validation%`&#39;作為&#39;`end_validation`&quot;
* &quot;`%INFO: Enable cron%`&#39;作為&#39;`enable_cron`&quot;
* &quot;`%INFO: Create backup of important files%`&#39;作為&#39;`create_backup`&quot;
* &quot;`%DEBUG: Step "backup" finished%`&#39;作為&#39;`backup_finished`&quot;
* &quot;`%INFO: Starting page warming up%`&#39;作為&#39;`warmup_start`&quot;
* &quot;`%ERROR: Warming up failed:%`&#39;作為&#39;`warm_up_fail`&quot;
* &quot;`%DEBUG: Step "warm-up" finished%`&#39;作為&#39;`warmup_finished`&quot;
* &quot;`%DEBUG: Step "time-to-first-byte" finished%`&#39;作為&#39;`ttfb_finished`&quot;
* &quot;`%INFO: Scenario(s) finished%`&#39;作為&#39;`post_deploy_finished`&quot;
* &quot;`%DEBUG: Running step: pre-build%`&#39;作為&#39;`run_pre-build`&quot;
* &quot;`%DEBUG: Flag .static_content_deploy has already been deleted%`&#39;作為&#39;`scd_flag_del`&quot;
* &quot;`%DEBUG: Step "pre-build" finished%`&#39;作為&#39;`pre-build_completed`&quot;
* &quot;`%NOTICE: Applying patches%`&#39;作為&#39;`apply_patches`&quot;
* &quot;`%has been applied%`&#39;作為&#39;`patches_applied`&quot;
* &quot;`%DEBUG: Step "apply-patches" finished%`&#39;作為&#39;`apply_patches_complete`&quot;
* &quot;`%Deploy using quick strategy%`&#39;作為&#39;`quick_strategy_deploy`&quot;
* &quot;`%NOTICE: Running DI compilation%`&#39;作為&#39;`di_compliation_start`&quot;
* &quot;`%NOTICE: End of running DI compilation%`&#39;作為&#39;`di_compliation_finished`&quot;
* &quot;`%NOTICE: Generating fresh static content%`&#39;作為&#39;`gen_frsh_static_content`&quot;
* &quot;`%magento setup:static-content:deploy%`&#39;作為&#39;`scd_executing`&quot;
* &quot;`%NOTICE: End of generating fresh static content%`&#39;作為&#39;`gen_frsh_static_cont_finished`&quot;
* &quot;`%INFO: Starting scenario(s): scenario/build/transfer.xml%`&#39;作為&#39;`start_transferxml`&quot;
* &quot;`%INFO: Trying to kill running cron jobs%`&#39;作為&#39;`kill_crons`&quot;
* &quot;`%INFO: Clearing redis cache:%`&#39;作為&#39;`clear_redis_cache`&quot;
* &quot;`%INFO: Checking if db exists and has tables%`&#39;作為&#39;`db_check`&quot;
* &quot;`%WARNING: [2010] Elasticsearch service is installed at infrastructure layer, but is not used as a search engine.%`作為「`es_not_used`&quot;
* &quot;`%NOTICE: Starting update.%`&#39;作為&#39;`starting_update`&quot;
* &quot;`%INFO: Set search engine to: mysql%`&#39;作為&#39;`mysql_search`&quot;
* &quot;`%SQLSTATE[HY000] [2006] MySQL server has gone away%`&#39;作為&#39;`mysql_gone`&quot;

## [!UICONTROL Count of modules imported during deploy]

![部署期間導入的模組計數](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

的 **[!UICONTROL Count of modules imported during deploy]** frame顯示在選定時間範圍內部署期間導入的模組數。

## [!UICONTROL Deployed module list]

![已部署模組清單](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

的 **[!UICONTROL Deployed module list]** frame顯示在選定時間範圍內部署的模組。
