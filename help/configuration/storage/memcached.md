---
title: 將memcached用於會話儲存
description: 瞭解如何將memcached用於Commerce會話儲存。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# 將memcached用於會話儲存

Memcached是一種通用的分佈式記憶體快取系統。 它通常用於通過在RAM中快取資料和對象來加快動態資料庫驅動網站的速度，以減少必須讀取外部資料源（如資料庫或API）的次數。

Memcached提供了一個大的哈希表，可以分佈在多台電腦中。 當表已滿時，後續插入會導致以最近最少使用的(LRU)順序清除舊資料。 此散清單的大小通常非常大。 (來源： [梅姆卡赫德組織](http://memcached.org/))

Commerce將memcached用於會話儲存，但不用於頁面快取。 對於頁面快取，我們建議 [雷迪斯](../cache/redis-pg-cache.md) 或 [清漆](../cache/config-varnish.md)。

**將Commerce配置為使用memcached**:

1. 開啟 `<your install dir>/app/etc/env.php` 的子菜單。
1. 找到以下內容：

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 按如下方式更改：

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached具有超出本指南範圍的可選啟動參數。 您可以在 [梅克謝](https://php.net/manual/en/memcached.sessions.php) 文檔、原始碼和更改日誌。

1. 繼續下一節。

**驗證memcached與Commerce的工作**:

1. 刪除Commerce安裝目錄下的以下目錄的內容：

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 轉到店面上的任何頁面。

1. 登錄到管理員並瀏覽到幾頁。

   如果沒有顯示錯誤，恭喜！ 梅姆卡切在工作！ 您可以選擇查看memcached儲存，如下一步中所述。

   如果顯示錯誤(如HTTP 500（內部伺服器錯誤）)，請啟用開發人員模式並診斷問題。 確保memcached正在運行，配置正確，並且 `env.php` 沒有語法錯誤。

1. （可選。） 使用Telnet查看Memcached儲存。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   結果顯示與以下內容類似：

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](http://www.darkcoding.net/software/memcached-list-all-keys/)
   ```
