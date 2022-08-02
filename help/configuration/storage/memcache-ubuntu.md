---
title: 在烏班圖上設定memcached
description: 在Ubuntu上安裝和配置memcached。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# 在烏班圖上設定memcached

本節提供在Ubuntu上安裝memcached的說明。

>[!INFO]
>
>Adobe建議使用memcached 3.0.5或更高版本。

由於PHP不支援memcache，因此必須安裝PHP的擴展才能使用它。 有兩個PHP擴展可用，對要使用的進行解碼非常重要：

- `memcache` (_沒有_) — 不定期維護的較舊但受歡迎的擴展。
的 `memcache` 當前擴展 _不_ 與7菲律賓比索一起工作。 請參閱 [memcache的PHP文檔](https://www.php.net/manual/en/book.memcache.php)。

   確切的名稱是 `php5-memcache` 烏班圖。

- `memcached` (_帶`d`_) — 與PHP 7相容的更新且維護的擴展。 請參閱 [PHP Memcached文檔](https://www.php.net/manual/en/book.memcached.php)。

   確切的名稱是 `php5-memcached` 烏班圖。

## 在Ubuntu上安裝和配置memcached

**在Ubuntu上安裝和配置memcached**:

1. 作為用戶 `root` 權限，輸入以下命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 更改的memcached配置設定 `CACHESIZE` 和 `-l`:

   1. 開啟 `/etc/memcached.conf` 的子菜單。
   1. 查找 `-m` 的下界。
   1. 將其值至少更改為 `1GB`
   1. 查找 `-l` 的下界。
   1. 將其值更改為 `127.0.0.1` 或 `localhost`
   1. 將更改保存到 `memcached.conf` 並退出文本編輯器。
   1. 重新啟動memcached。

      ```bash
      service memcached restart
      ```

1. 重新啟動Web伺服器。

   對於Apache, `service apache2 restart`

1. 繼續下一節。

## 在安裝Magento之前驗證memcached是否工作

Adobe建議在安裝Commerce之前測試memcached以確保它工作。 這樣做只需幾分鐘，可以簡化以後的故障排除。

### 驗證Web伺服器是否識別memcached

要驗證Web伺服器是否識別memcached，請執行以下操作：

1. 建立 `phpinfo.php` Web伺服器的docroot中的檔案：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在Web瀏覽器中轉到該頁面。 例如：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. 確保memcached顯示如下：

   ![確認Web伺服器已識別Memcached](../../assets/configuration/memcache.png)

   驗證您使用的是memcached 3.0.5版或更高版本。

   如果memcached未顯示，請重新啟動Web伺服器並刷新瀏覽器頁。 如果仍未顯示，請驗證是否已安裝 `php-pecl-memcached` 擴展。

### 驗證memcached是否可快取資料

此test使用PHP指令碼驗證memcached是否可以儲存和檢索 [快取](https://glossary.magento.com/cache) 資料。

有關此test的詳細資訊，請參見 [如何在Ubuntu教程中安裝和使用Memcache](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04)。

建立 `cache-test.php` 在Web伺服器的docroot中，包含以下內容：

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

位置 `<memcached hostname or ip>` 或 `localhost`。 `127.0.0.1`，或memcache主機名或IP地址。 的 `<memcached port>` 是監聽埠；預設情況下， `11211`。

在Web瀏覽器中轉到該頁。 例如

```http
http://192.0.2.1/cache-test.php
```

首次轉到頁面時，將顯示以下內容： `No matching key found. Refresh the browser to add it!`

刷新瀏覽器。 消息更改為 `Successfully retrieved the data!`

最後，您可以使用Telnet查看memcache密鑰：

```bash
telnet localhost <memcache port>
```

在提示符下，輸入

```shell
stats items
```

結果與以下內容類似：

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

[有關Telnettest的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
