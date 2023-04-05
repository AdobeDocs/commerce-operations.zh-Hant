---
title: 在Ubuntu上設定memcached
description: 在Ubuntu上安裝並配置memcached。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# 在Ubuntu上設定memcached

本節提供在Ubuntu上安裝memcached的說明。

>[!INFO]
>
>Adobe建議使用memcached 3.0.5版或更新版本。

由於PHP不支援memcache，因此您必須安裝PHP的擴展才能使用它。 有兩個PHP擴充功能可供使用，請務必將要使用的擴充功能解碼：

- `memcache` (_no d_) — 較舊但受歡迎的擴充功能，不會定期維護。
此 `memcache` 目前擴充功能 _不_ 與PHP 7搭配使用。 請參閱 [門快取的PHP文檔](https://www.php.net/manual/en/book.memcache.php).

   確切名稱為 `php5-memcache` 為烏邦圖。

- `memcached` (_帶`d`_) — 與PHP 7相容的較新且維護的擴充功能。 請參閱 [memcached的PHP文檔](https://www.php.net/manual/en/book.memcached.php).

   確切名稱為 `php5-memcached` 為烏邦圖。

## 在Ubuntu上安裝和配置memcached

**在Ubuntu上安裝和配置memcached**:

1. 身為使用者 `root` 權限，輸入以下命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 更改的memcached配置設定 `CACHESIZE` 和 `-l`:

   1. 開啟 `/etc/memcached.conf` 在文字編輯器中。
   1. 找出 `-m` 參數。
   1. 至少將其值變更為 `1GB`
   1. 找出 `-l` 參數。
   1. 將其值變更為 `127.0.0.1` 或 `localhost`
   1. 將變更儲存至 `memcached.conf` 並退出文字編輯器。
   1. 重新啟動memcached。

      ```bash
      service memcached restart
      ```

1. 重新啟動Web伺服器。

   若為Apache, `service apache2 restart`

1. 繼續下一節。

## 在安裝Magento之前驗證memcached工作

Adobe建議先測試memcached，以在您安裝商務前確定它有效。 這麼做只需幾分鐘的時間，日後可簡化疑難排解。

### 驗證Web伺服器是否識別mmcached

要驗證Web伺服器是否識別Memcached:

1. 建立 `phpinfo.php` 檔案（位於Web伺服器的docroot中）:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在網頁瀏覽器中前往該頁面。 例如：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. 請確定memcached顯示如下：

   ![確認Web伺服器已識別mmcached](../../assets/configuration/memcache.png)

   確認您使用的是memcached 3.0.5版或更新版本。

   如果未顯示Memcached，請重新啟動Web伺服器並刷新瀏覽器頁。 如果仍未顯示，請確認您已安裝 `php-pecl-memcached` 擴充功能。

### 驗證memcached可以快取資料

此測試使用PHP指令碼來驗證Memcached是否可以儲存和檢索快取資料。

如需此測試的詳細資訊，請參閱 [如何在Ubuntu教學課程上安裝和使用Memcache](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

建立 `cache-test.php` 在Web伺服器的資料夾中，包含下列內容：

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

其中 `<memcached hostname or ip>` 為 `localhost`, `127.0.0.1`，或memcache主機名或IP地址。 此 `<memcached port>` 是監聽埠；依預設， `11211`.

在網頁瀏覽器中前往該頁面。 例如

```http
http://192.0.2.1/cache-test.php
```

第一次前往頁面時，會顯示下列內容： `No matching key found. Refresh the browser to add it!`

重新整理瀏覽器。 訊息會變更為 `Successfully retrieved the data!`

最後，您可以使用Telnet查看記憶體快取密鑰：

```bash
telnet localhost <memcache port>
```

在提示符下，輸入

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

刷新Memcached儲存並退出Telnet:

```shell
flush_all
```

```shell
quit
```

[有關Telnet測試的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
