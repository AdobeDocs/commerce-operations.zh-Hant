---
user-guide-title: 配置指南
user-guide-description: 配置您的Adobe Commerce或Magento Open Source應用程式功能和服務。
feature: Configuration
source-git-commit: 68c4cfc29735d2ea296f579ed0a0ff52db3fdd9f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# 配置指南 {#configuration-guide}

+ [概述](overview.md)
+ 常規設定 {#setup}
   + [應用程式初始化和引導](bootstrap/initialization.md)
   + [應用模式](bootstrap/application-modes.md)
   + [Bootstrap參數](bootstrap/set-parameters.md)
   + [分析](bootstrap/mage-profiler.md)
   + [基本目錄路徑](bootstrap/mage-directory.md)
+ 部署 {#deployment}
   + [部署概述](deployment/overview.md)
   + [單機部署](deployment/single-machine.md)
   + [管道部署](deployment/technical-details.md)
   + [先決條件](deployment/prerequisites.md)
   + [開發系統設定](deployment/development-system.md)
   + [生成系統設定](deployment/build-system.md)
   + [生產系統設定](deployment/production-system.md)
   + [檔案系統訪問權限](deployment/file-system-permissions.md)
   + 示例 {#examples}
      + [使用共用配置](deployment/example-shared-configuration.md)
      + [使用CLI命令](deployment/example-using-cli.md)
      + [使用環境變數](deployment/example-environment-variables.md)
+ 快取 {#cache}
   + [快取概述](cache/caching-overview.md)
   + [快取類型](cache/cache-types.md)
   + [快取選項](cache/cache-options.md)
   + [二級快取](cache/level-two-cache.md)
   + 雷迪斯 {#redis}
      + [配置密文](cache/config-redis.md)
      + [將Redis用於預設快取](cache/redis-pg-cache.md)
      + [將Redis用於會話儲存](cache/redis-session.md)
   + 清漆 {#varnish}
      + [清漆概述](cache/config-varnish.md)
      + [安裝清漆](cache/config-varnish-install.md)
   + [Web伺服器](cache/config-varnish-server.md)
   + [配置Commerce應用程式](cache/configure-varnish-commerce.md)
   + [高級清漆配置](cache/config-varnish-advanced.md)
   + [快取清除](cache/use-varnish-cache.md)
   + [快取清除多個清漆實例](cache/use-multiple-varnish-cache.md)
   + [驗證清漆配置](cache/config-varnish-final.md)
   + [清漆ESI塊](cache/use-varnish-esi.md)
   + [靜態內容快取](cache/static-content-signing.md)
+ 命令行 {#cli}
   + [命令行工具](cli/config-cli.md)
   + [常用命令](cli/common-cli-commands.md)
   + [啟用日誌記錄](cli/enable-logging.md)
   + [管理快取](cli/manage-cache.md)
   + [管理索引器](cli/manage-indexers.md)
   + [配置cron作業](cli/configure-cron-jobs.md)
   + [編譯代碼](cli/code-compiler.md)
   + [操作模式](cli/set-mode.md)
   + [啟動消息隊列使用者](cli/start-message-queues.md)
   + [URN螢光筆](cli/urn-highlighter.md)
   + [依賴關係報告](cli/dependency-reports.md)
   + [本地化](cli/localization.md)
   + 配置管理 {#configuration-management}
      + [設定值](cli/set-configuration-values.md)
      + [導出設定](cli/export-configuration.md)
      + [導入資料](cli/import-configuration.md)
   + 靜態視圖 {#static-view}
      + [部署策略](cli/static-view-file-strategy.md)
      + [部署靜態視圖檔案](cli/static-view-file-deployment.md)
   + [建立符號連結](cli/create-symlinks.md)
   + [運行單位test](cli/unit-tests.md)
   + [轉換佈局檔案](cli/convert-layout-files.md)
   + [生成資料以進行效能測試](cli/generate-data.md)
   + [運行支援實用程式（僅限Commerce）](cli/run-support-utilities.md)
+ 配置檔案 {#files}
   + [部署的配置檔案](reference/deployment-files.md)
   + [配置類型](reference/config-create-types.md)
   + [模組檔案](reference/module-files.md)
   + [模組輸出](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [吉格諾](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 配置路徑 {#paths}
   + [常規](reference/config-reference-general.md)
   + [B2B擴展](reference/config-reference-b2b.md)
   + [目錄](reference/config-reference-catalog.md)
   + [客戶](reference/config-reference-customers.md)
   + [付款方法](reference/config-reference-payment.md)
   + [銷售](reference/config-reference-sales.md)
   + [服務](reference/config-reference-services.md)
   + [敏感和系統特定設定](reference/config-reference-sens.md)
   + [覆蓋配置設定](reference/override-config-settings.md)
+ 克龍·喬布斯 {#crons}
   + [Cron作業和組](cron/custom-cron.md)
   + [自定義crons引用](cron/custom-cron-reference.md)
   + [配置自定義cron作業](cron/custom-cron-tutorial.md)
+ 日誌 {#logs}
   + [自定義日誌](logs/custom-logging.md)
   + [記錄器介面](logs/logger-interface.md)
   + [日誌資料庫活動](logs/database-activity.md)
   + [寫入自定義日誌檔案](logs/custom-log-files.md)
+ 消息隊列 {#message-queues}
   + [消息隊列框架](queues/message-queue-framework.md)
   + [管理消息隊列](queues/manage-message-queues.md)
   + [設定AmazonMQ](queues/aws-mq.md)
   + [消費者](queues/consumers.md)
+ 多個站點 {#multi-sites}
   + [多個站點和視圖](multi-sites/ms-overview.md)
   + [資料庫實體增量ID](multi-sites/change-increment-id.md)
   + [在管理員中設定](multi-sites/ms-admin.md)
   + [設定為Nginx](multi-sites/ms-nginx.md)
   + [使用Apache設定](multi-sites/ms-apache.md)
+ 搜索引擎 {#search}
   + [搜索引擎概述](search/overview-search.md)
   + [配置搜索引擎](search/configure-search-engine.md)
   + [帶止字的過濾器](search/search-stopwords.md)
+ 安全 {#security}
   + [安全概述](security/overview.md)
   + [密碼散列](security/password-hashing.md)
   + [快取中毒](security/cache-poisoning.md)
   + [安全Cron PHP](security/secure-cron-php.md)
   + [安全TXT](security/security-txt.md)
   + [X — 幀 — 選項標題](security/xframe-options.md)
+ 儲存 {#storage}
   + [資料庫探查器](storage/db-profiler.md)
   + 遠程儲存 {#remote-storage}
      + [遠程儲存模組](remote-storage/remote-storage.md)
      + [AWSS3桶](remote-storage/remote-storage-aws-s3.md)
      + [調整影像大小](remote-storage/remote-storage-image-resize.md)
      + [雲的遠程儲存](remote-storage/cloud-support.md)
   + 會話儲存 {#session-storage}
      + [會話儲存位置](storage/sessions.md)
      + [會話儲存的memcached](storage/memcached.md)
      + [CentOS上的memcached](storage/memcache-centos.md)
      + [梅姆卡什在烏本圖](storage/memcache-ubuntu.md)
   + 拆分資料庫 {#split-db}
      + [拆分資料庫概述](storage/multi-master.md)
      + [自動配置](storage/multi-master-masterdb.md)
      + [手動配置](storage/multi-master-manual.md)
      + [驗證剝離資料庫](storage/multi-master-verify.md)
      + [資料庫複製](storage/multi-master-replication.md)
      + [還原到單個資料庫](storage/revert-split-database.md)
+ [返回操作指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)