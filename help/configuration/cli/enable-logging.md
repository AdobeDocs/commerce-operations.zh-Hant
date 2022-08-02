---
title: 啟用日誌記錄
description: 瞭解如何啟用和禁用記錄類型。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 啟用日誌記錄

{{file-system-owner}}

## 調試日誌記錄

預設情況下，Commerce將寫入調試日誌(`<install_directory>/var/log/debug.log`)，而不是處於生產模式。 使用 `bin/magento setup:config:set --enable-debug-logging` 的子菜單。

>[!INFO]
>
>從Commerce 2.3.1開始，您不能再使用 `bin/magento config:set dev/debug/debug_logging` 命令，以啟用或禁用當前模式的調試日誌記錄。

### 啟用調試日誌記錄

1. 使用 `setup:config:set` 命令，以啟用當前模式的調試日誌記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 刷新快取。

   ```bash
   bin/magento cache:flush
   ```

### 禁用調試日誌記錄

1. 使用 `setup:config:set` 命令禁用當前模式的調試日誌記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 刷新快取。

   ```bash
   bin/magento cache:flush
   ```

## 資料庫日誌

預設情況下，Commerce將資料庫活動日誌寫入 `<install-dir>/var/debug/db.log` 的子菜單。

### 啟用資料庫日誌記錄

1. 使用 `dev:query-log` 命令以啟用或禁用資料庫日誌記錄。

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. 刷新快取。

   ```bash
   bin/magento cache:flush
   ```

## Cron日誌記錄

隨著版本2.3.1的發佈，Commerce現在會建立一個 `cron` 日誌。 \
最近，Commerce使cron日誌更加冗餘，這提供了更多資訊，但延長了 `system.log` 相當多。
移動 `cron` 通過向專用日誌提供資訊，可以更輕鬆地讀取這兩個日誌。

預設情況下，Commerce寫入 `cron` 資訊 `<install-directory>/var/log/cron.log` 的子菜單。

## Syslog日誌記錄

預設情況下，Commerce寫入 _系統_ 登錄到作業系統 `syslog` 的子菜單。
自Commerce 2.3.1起，您必須使用 `magento` 命令以啟用或禁用syslog。
已刪除管理員中的設定。

### 啟用syslog日誌記錄

登錄到 `syslog` 預設情況下為禁用。

1. 使用 `setup:config:set` 命令 `dev/syslog/syslog_logging` 資料庫值 `true`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 刷新快取。

   ```bash
   bin/magento cache:flush
   ```

### 禁用syslog日誌記錄

1. 使用 `setup:config:set` 命令 `dev/syslog/syslog_logging` 資料庫值 `false`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 刷新快取。

   ```bash
   bin/magento cache:flush
   ```
