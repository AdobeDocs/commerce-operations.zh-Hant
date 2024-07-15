---
title: 將記憶體快取用於工作階段儲存
description: 瞭解如何將memcached用於Commerce工作階段存放區。
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 將記憶體快取用於工作階段儲存

Memcached是一種通用分散式記憶體快取系統。 它通常用來加速動態資料庫驅動的網站，方法是在RAM中快取資料和物件，以減少必須讀取外部資料來源（例如資料庫或API）的次數。

Memcached提供大型雜湊表，可以分佈在多部機器上。 當表格已滿時，後續的插入會以最近最少使用的(LRU)順序清除較舊的資料。 此雜湊表格的大小通常非常大。 (Source： [memcached.org](https://www.memcached.org/))

Commerce會將memcached用於工作階段儲存，但不會用於頁面快取。 針對頁面快取，我們建議[Redis](../cache/redis-pg-cache.md)或[Varnish](../cache/config-varnish.md)。

**若要設定Commerce使用memcached**：

1. 在文字編輯器中開啟`<your install dir>/app/etc/env.php`。
1. 找出下列專案：

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 請依照以下步驟變更：

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached有本指南範圍以外的選擇性啟動引數。 您可以在[memcached](https://www.php.net/manual/en/memcached.sessions.php)檔案、原始程式碼和變更記錄檔中找到有關它們的詳細資訊。

1. 繼續下一節。

**若要驗證memcached是否適用於Commerce**：

1. 刪除Commerce安裝目錄下下列目錄的內容：

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 前往店面上的任何頁面。

1. 登入「管理員」並瀏覽至數個頁面。

   如果沒有顯示錯誤，恭喜您！ memcached正在運作！ 您可以選擇檢視記憶體快取儲存體，如同下個步驟所述。

   如果顯示錯誤(例如HTTP 500 （內部伺服器錯誤）)，請啟用開發人員模式並診斷問題。 請確定memcached正在執行、設定正確，而且`env.php`沒有語法錯誤。

1. （選擇性。） 使用Telnet檢視記憶體快取儲存體。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   結果顯示類似以下內容：

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
