---
title: 在Ubuntu上設定memcached
description: 在Ubuntu上安裝並設定memcached。
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 在Ubuntu上設定memcached

本節提供在Ubuntu上安裝memcached的說明。

>[!INFO]
>
>Adobe建議使用memcached 3.0.5版或更新版本。

因為PHP對memcache沒有原生支援，所以您必須安裝擴充功能以供PHP使用。 有兩個可用的PHP擴充功能，請務必解碼要使用哪個：

- `memcache` (_no d_) — 不是定期維護的舊版但常用的擴充功能。
`memcache`延伸模組目前&#x200B;_不適用於PHP 7。_ 請參閱memcache[&#128279;](https://www.php.net/manual/en/book.memcache.php)的PHP檔案。

  Ubuntu的確切名稱是`php5-memcache`。

- `memcached` （_具有`d`_） — 與PHP 7相容的較新且已維護的擴充功能。 請參閱memcached[&#128279;](https://www.php.net/manual/en/book.memcached.php)的PHP檔案。

  Ubuntu的確切名稱是`php5-memcached`。

## 在Ubuntu上安裝並設定memcached

**若要在Ubuntu上安裝並設定memcached**：

1. 以具有`root`許可權的使用者身分，輸入下列命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 變更`CACHESIZE`和`-l`的memcached組態設定：

   1. 在文字編輯器中開啟`/etc/memcached.conf`。
   1. 找到`-m`引數。
   1. 將其值變更為至少`1GB`
   1. 找到`-l`引數。
   1. 將其值變更為`127.0.0.1`或`localhost`
   1. 將變更儲存至`memcached.conf`並結束文字編輯器。
   1. 重新啟動memcached。

      ```bash
      service memcached restart
      ```

1. 重新啟動您的網頁伺服器。

   針對Apache，`service apache2 restart`

1. 繼續下一節。

## 在安裝Magento之前驗證memcached的運作方式

Adobe建議先測試memcached以確保其可運作，然後再安裝Commerce。 只需幾分鐘即可完成這項工作，並可簡化後續的疑難排解。

### 驗證Web伺服器是否可辨識memcached

若要確認網頁伺服器可辨識memcached：

1. 在網頁伺服器的docroot中建立`phpinfo.php`檔案：

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

   ![確認網頁伺服器可辨識memcached](../../assets/configuration/memcache.png)

   確認您使用的是memcached 3.0.5版或更新版本。

   如果memcached未顯示，請重新啟動網頁伺服器並重新整理瀏覽器頁面。 如果仍然未顯示，請確認您已安裝`php-pecl-memcached`擴充功能。

### 驗證memcached可以快取資料

此測試使用PHP指令碼來驗證memcached可以儲存和擷取快取資料。

如需此測試的詳細資訊，請參閱[如何在Ubuntu教學課程中安裝及使用Memcache ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04)。

在網頁伺服器的docroot中建立`cache-test.php`，其內容如下：

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

其中`<memcached hostname or ip>`是`localhost`、`127.0.0.1`或memcache主機名稱或IP位址。 `<memcached port>`是接聽連線埠；預設為`11211`。

在網頁瀏覽器中前往該頁面。 例如

```http
http://192.0.2.1/cache-test.php
```

第一次前往頁面時，會顯示下列專案： `No matching key found. Refresh the browser to add it!`

重新整理瀏覽器。 訊息變更為`Successfully retrieved the data!`

最後，您可以使用Telnet檢視memcache金鑰：

```bash
telnet localhost <memcache port>
```

出現提示時，輸入

```shell
stats items
```

結果類似下列：

```
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

[有關Telnet測試的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
