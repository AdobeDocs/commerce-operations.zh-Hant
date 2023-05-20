---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生產系統

**更新生產系統**:

1. 以檔案系統所有者身份登錄到生產系統。
1. 更改為應用程式根並啟用維護模式。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   有關其他選項（如設定IP地址白名單的能力），請參見 [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)。

1. 通過設定來停止任何正在運行的隊列工作程式 `cron_run` 至 `false` 在 `app/etc/env.php` 如下：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新配置。

   ```bash
   bin/magento app:config:import
   ```

1. 終於， `kill` 任何活動的使用者進程。

   ```bash
   kill <PID>
   ```

   位置 `PID` 是要終止的進程ID，例如：

   ```bash
   kill 1234
   ```

1. 從原始碼管理中提取代碼。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 更新配置。

   ```bash
   bin/magento app:config:import
   ```

1. 清除快取。

   ```bash
   bin/magento cache:clean
   ```

1. 結束維護模式。

   ```bash
   bin/magento maintenance:disable
   ```
