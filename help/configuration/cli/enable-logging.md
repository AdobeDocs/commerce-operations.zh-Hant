---
title: 啟用記錄
description: 瞭解如何在Adobe Commerce中啟用和停用不同型別的登入。 探索記錄設定和管理技術。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# 啟用記錄

{{file-system-owner}}

## 偵錯記錄

依預設，Commerce在預設或開發模式中寫入偵錯記錄(`<install_directory>/var/log/debug.log`)，但在生產模式中則不寫入。 使用`bin/magento setup:config:set --enable-debug-logging`命令變更預設值。

>[!INFO]
>
>自Commerce 2.3.1起，您無法再使用`bin/magento config:set dev/debug/debug_logging`命令來啟用或停用目前模式的偵錯記錄。

### 啟用偵錯記錄

1. 使用`setup:config:set`命令啟用目前模式的偵錯記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 排清快取。

   ```bash
   bin/magento cache:flush
   ```

### 停用偵錯記錄

1. 使用`setup:config:set`命令停用目前模式的偵錯記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 排清快取。

   ```bash
   bin/magento cache:flush
   ```

## 資料庫記錄

依預設，Commerce會將資料庫活動記錄檔寫入`<install-dir>/var/debug/db.log`檔案。

### 啟用資料庫記錄

1. 使用`dev:query-log`命令來啟用或停用資料庫記錄。

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. 排清快取。

   ```bash
   bin/magento cache:flush
   ```

## Cron記錄

隨著2.3.1版的發行，Commerce現在會建立個別的`cron`記錄。 \
Commerce最近讓cron記錄更詳細，這提供了更多資訊，但大幅延長了`system.log`。
將`cron`資訊移至專用記錄檔可讓兩個記錄檔更容易閱讀。

依預設，Commerce會將`cron`資訊寫入`<install-directory>/var/log/cron.log`檔案。

## Syslog記錄

依預設，Commerce會將&#x200B;_syslog_&#x200B;記錄檔寫入作業系統`syslog`檔案。
自Commerce 2.3.1起，您必須使用`magento`命令來啟用或停用syslog。
管理員中的設定已移除。

### 啟用syslog記錄

預設會停用登入`syslog`。

1. 使用`setup:config:set`命令將`dev/syslog/syslog_logging`資料庫值變更為`true`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 排清快取。

   ```bash
   bin/magento cache:flush
   ```

### 停用syslog記錄

1. 使用`setup:config:set`命令將`dev/syslog/syslog_logging`資料庫值變更為`false`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 排清快取。

   ```bash
   bin/magento cache:flush
   ```
