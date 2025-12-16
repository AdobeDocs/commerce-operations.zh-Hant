---
title: 從RabbitMQ移轉至ActiveMQ
description: 瞭解如何取代用於Adobe Commerce內部部署安裝的訊息佇列代理人。
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# 移轉至ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis)是高效能、多通訊協定訊息代理人，可作為RabbitMQ的替代方案，用於處理Adobe Commerce中的訊息佇列。

截至2.4.8-p3、2.4.7-p8、2.4.6-p13和2.4.5-p16，Adobe Commerce支援ActiveMQ作為訊息佇列代理人。 這可讓內部部署安裝根據基礎架構需求和專業知識，在RabbitMQ和ActiveMQ之間做出選擇。

## 開始之前

開始移轉之前，請確定下列事項：

1. 在`app/etc/env.php`中檢閱您目前的RabbitMQ設定。
1. 對資料庫和程式碼基底進行完整備份。
1. 確定您的安裝符合ActiveMQ的系統需求。
1. 規劃維護期間以完成移轉。

## 移轉路徑

移轉至ActiveMQ是簡單直接的程式，但在切換代理人之前，請務必確認所有待處理的訊息都已處理。

這些移轉指示假設Adobe Commerce是使用訊息佇列代理程式的唯一應用程式。

### 步驟1：將網站置於維護模式

1. 將網站置於[維護模式](../../installation/tutorials/maintenance-mode.md)：

   ```bash
   bin/magento maintenance:enable
   ```

1. 確認維護模式已啟用：

   ```bash
   bin/magento maintenance:status
   ```

### 步驟2：檢查RabbitMQ訊息計數

繼續之前，請確認RabbitMQ中的所有訊息均已處理完畢。 使用下列其中一種方法：

#### 方法A：使用RabbitMQ管理控制面板

1. 在`http://<host>:15672`存取RabbitMQ管理UI
1. 預設認證： `guest/guest`
1. 瀏覽至&#x200B;**佇列**&#x200B;索引標籤
1. 驗證所有佇列是否顯示&#x200B;**0則訊息**

   ![RabbitMQ管理儀表板](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### 方法B：使用rabbitmqctl命令列

1. 檢查所有佇列及其訊息計數：

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="RabbitMQ CLI輸出" width="500" />

1. 檢查詳細的佇列資訊：

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="RabbitMQ CLI詳細輸出" width="500" />

### 步驟3：處理待處理的訊息

如果訊息在任何佇列中處於擱置狀態，請先處理這些訊息再繼續。

1. 取得可用的消費者清單：

   ```bash
   bin/magento queue:consumers:list
   ```

1. 以群組或個別訊息佇列方式處理使用者：

   - **將消費者處理為群組**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >如果系統中已執行cron，則不需要手動執行`bin/magento cron:run --group=consumers`。 相反地，透過使用步驟2中的命令檢查訊息計數，以確認訊息正在處理中。

   - **處理特定訊息佇列**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     例如，若要處理非同步操作，請執行下列動作：

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >`--max-messages`引數會限制消費者停止前要處理的訊息數目。 根據您的佇列大小調整此值。

   - **監視訊息處理**

     持續檢查訊息計數，直到所有佇列都為空白：

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### 步驟4：確認已處理所有訊息

繼續下一步前，請確定&#x200B;**所有佇列都顯示0則訊息**。 再次執行步驟2中的驗證命令。

>[!WARNING]
>
>如果有任何訊息仍未處理，請勿繼續進行下一個步驟。 如果您在訊息仍擱置時切換代理人，可能會發生資料遺失。

### 步驟5：停止消費者和cron工作

1. 停止所有執行中的訊息佇列取用者：

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. 停用cron工作：

   ```bash
   bin/magento cron:remove
   ```

1. 確認cron工作已移除：

   ```bash
   crontab -l
   ```

### 步驟6：備份目前的設定

建立目前設定的備份：

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### 步驟7：選擇性解除安裝RabbitMQ

如果不再需要使用RabbitMQ，您可以解除安裝。

### 步驟8：在Adobe Commerce中安裝和設定ActiveMQ

若要完成ActiveMQ安裝與設定工作，例如設定STOMP通訊協定及驗證連線，請參閱[安裝與設定指南](../../installation/prerequisites/activemq.md)。

### 步驟9：重新安裝cron工作

1. 測試成功完成後，重新安裝cron作業：

   ```bash
   bin/magento cron:install
   ```

1. 確認cron工作已排程：

   ```bash
   crontab -l
   ```

### 步驟10：停用維護模式

1. 確認一切都正常運作後，請停用維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

1. 確認維護模式已停用：

   ```bash
   bin/magento maintenance:status
   ```

### 步驟11：監視系統

在移轉後24到48小時內監視您的系統，以確保所有佇列作業都正常運作：

- 請定期檢查ActiveMQ Web Console的訊息輸送量
- 監視應用程式記錄檔中的佇列相關錯誤
- 驗證非同步操作（設定儲存、匯出等）是否正常運作
- 檢查cron記錄檔以確保消費者執行中

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## 回覆

如果移轉期間或移轉後發生問題，您可以復原至RabbitMQ：

1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 停止所有消費者並停用cron：

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. 還原先前的設定：

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. 啟動RabbitMQ （如果停止）：

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. 清除快取：

   ```bash
   bin/magento cache:flush
   ```

1. 重新安裝cron：

   ```bash
   bin/magento cron:install
   ```

1. 停用維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

完成移轉後，不需要進一步變更設定值。

