---
title: 在Ubuntu上設定memcached
description: 在Ubuntu上安裝並設定memcached。
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 在Ubuntu上設定memcached

本節提供在Ubuntu上安裝memcached的說明。

>[!INFO]
>
>Adobe建議使用memcached 3.0.5版或更新版本。

因為PHP對memcache沒有原生支援，所以您必須安裝擴充功能以供PHP使用。 有兩個可用的PHP擴充功能，請務必解碼要使用哪個：

- `memcache` (_否d_) — 舊版但常用的擴充功能，不會定期維護。
此 `memcache` 目前為擴充功能 _不會_ 使用PHP 7。 另請參閱 [memcache的PHP檔案](https://www.php.net/manual/en/book.memcache.php).

  確切名稱為 `php5-memcache` 適用於Ubuntu。

- `memcached` (_與`d`_) — 與PHP 7相容的較新及維護的擴充功能。 另請參閱 [memcached的PHP檔案](https://www.php.net/manual/en/book.memcached.php).

  確切名稱為 `php5-memcached` 適用於Ubuntu。

## 在Ubuntu上安裝並設定memcached

**若要在Ubuntu上安裝和設定記憶體**：

1. 作為使用者，具有 `root` 許可權，請輸入以下命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 變更的memcached組態設定 `CACHESIZE` 和 `-l`：

   1. 開啟 `/etc/memcached.conf` 在文字編輯器中。
   1. 找到 `-m` 引數。
   1. 至少將其值變更為 `1GB`
   1. 找到 `-l` 引數。
   1. 將其值變更為 `127.0.0.1` 或 `localhost`
   1. 將變更儲存至 `memcached.conf` 並退出文字編輯器。
   1. 重新啟動memcached。

      ```bash
      service memcached restart
      ```

1. 重新啟動您的網頁伺服器。

   對於Apache， `service apache2 restart`

1. 繼續下一節。

## 在安裝Magento之前驗證memcached的運作方式

Adobe建議先測試memcached以確保其可運作，然後再安裝Commerce。 只需幾分鐘即可完成這項工作，並可簡化後續的疑難排解。

### 驗證Web伺服器是否可辨識memcached

若要確認網頁伺服器可辨識memcached：

1. 建立 `phpinfo.php` 網頁伺服器的docroot中的檔案：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 前往網頁瀏覽器中的該頁面。 例如：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. 請確定memcached顯示如下：

   ![確認網頁伺服器可辨識成員快取](../../assets/configuration/memcache.png)

   確認您使用的是memcached 3.0.5版或更新版本。

   如果memcached未顯示，請重新啟動網頁伺服器並重新整理瀏覽器頁面。 如果仍然沒有顯示，請確認您已安裝 `php-pecl-memcached` 副檔名。

### 驗證memcached可以快取資料

此測試使用PHP指令碼來驗證memcached可以儲存和擷取快取資料。

如需此測試的詳細資訊，請參閱 [如何在Ubuntu教學課程上安裝和使用Memcache](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

建立 `cache-test.php` 網頁伺服器的docroot中包含下列內容：

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

位置 `<memcached hostname or ip>` 是 `localhost`， `127.0.0.1`、或memcache主機名稱或IP位址。 此 `<memcached port>` 是監聽連線埠；預設為 `11211`.

在網頁瀏覽器中前往該頁面。 例如

```http
http://192.0.2.1/cache-test.php
```

第一次前往頁面時，會顯示下列內容： `No matching key found. Refresh the browser to add it!`

重新整理瀏覽器。 訊息將變更為 `Successfully retrieved the data!`

最後，您可以使用Telnet檢視memcache金鑰：

```bash
telnet localhost <memcache port>
```

出現提示時，輸入

```shell
stats items
```

結果類似下列：

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

排清成員快取儲存體並結束Telnet：

```shell
flush_all
```

```shell
quit
```

[Telnet測試的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
