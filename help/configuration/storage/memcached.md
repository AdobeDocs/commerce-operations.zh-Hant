---
title: 將memcached用於會話儲存
description: 了解如何將memcached用於商務會話儲存。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# 將memcached用於會話儲存

Memcached是一種通用的分佈式記憶體快取系統。 它通常用於快取RAM中的資料和物件，以加速動態資料庫驅動的網站，以減少必須讀取外部資料源（例如資料庫或API）的次數。

Memcached提供了一個大的哈希表，可以跨多台電腦分佈。 當表已滿時，後續插入會導致以最近使用的(LRU)順序清除較舊的資料。 此雜湊表的大小通常很大。 (來源： [memcached.org](https://www.memcached.org/))

商務會使用MemcAched來儲存工作階段，但不會使用Page Caching。 針對頁面快取，建議 [雷迪斯](../cache/redis-pg-cache.md) 或 [清漆](../cache/config-varnish.md).

**要配置商務以使用memcached**:

1. 開啟 `<your install dir>/app/etc/env.php` 在文字編輯器中。
1. 找出下列項目：

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 變更如下：

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached具有超出本指南範圍的可選啟動參數。 您可以在 [memcached](https://www.php.net/manual/en/memcached.sessions.php) 檔案、原始碼和變更記錄。

1. 繼續下一節。

**驗證Memcached與Commerce的工作**:

1. 刪除Commerce安裝目錄下的以下目錄的內容：

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 轉到店面上的任何頁面。

1. 登入管理員並瀏覽至數個頁面。

   如果沒有顯示錯誤，恭喜！ 梅姆卡奇在工作！ 您可以選擇查看成組快取儲存，如下一步所述。

   如果顯示錯誤(例如HTTP 500（內部伺服器錯誤）)，請啟用開發人員模式並診斷問題。 請確定memcached正在運行、已正確配置，並且 `env.php` 沒有語法錯誤。

1. （可選。） 使用Telnet查看磁碟快取儲存。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   結果顯示如下：

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
