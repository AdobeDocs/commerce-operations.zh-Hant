---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 更新生產系統

**更新生產系統**:

1. 以檔案系統擁有者身分登入生產系統。
1. 更改應用程式根目錄並啟用維護模式。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   如需其他選項，例如設定IP位址白名單的功能，請參閱 [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. 通過設定 `cron_run` to `false` in `app/etc/env.php` 如下所示：

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 更新設定。

   ```bash
   bin/magento app:config:import
   ```

1. 最後， `kill` 任何使用中的消費者程式。

   ```bash
   kill <PID>
   ```

   其中 `PID` 會終止處理程式ID，例如：

   ```bash
   kill 1234
   ```

1. 從原始碼控制項提取代碼。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 更新設定。

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
