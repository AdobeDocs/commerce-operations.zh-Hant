---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生產系統

**若要更新生產系統**：

1. 以檔案系統擁有者的身分登入生產系統。
1. 變更為應用程式根並啟用維護模式。

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   如需其他選項，例如設定IP位址白名單的功能，請參閱[`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)。

1. 透過在`app/etc/env.php`中將`cron_run`設定為`false`來停止任何執行中的佇列背景工作，如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新設定。

   ```shell
   bin/magento app:config:import
   ```

1. 最後，`kill`任何使用中的消費者處理序。

   ```shell
   kill <PID>
   ```

   其中`PID`是要終止的處理序識別碼，例如：

   ```shell
   kill 1234
   ```

1. 從原始檔控制提取程式碼。

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. 更新設定。

   ```shell
   bin/magento app:config:import
   ```

1. 清除快取。

   ```shell
   bin/magento cache:clean
   ```

1. 結束維護模式。

   ```shell
   bin/magento maintenance:disable
   ```
