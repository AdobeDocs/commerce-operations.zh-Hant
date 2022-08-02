---
title: 在CentOS上設定memcached
description: 在CentOS上安裝和配置memcached。
source-git-commit: 65060d067bbbfe139736df3800688ce897cb17be
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# 在CentOS上設定memcached

本節提供在CentOS上安裝memcached的說明。 有關其他資訊，請參閱 [麥克切維基](https://github.com/memcached/old-wiki)。

>[!INFO]
>
>Adobe建議使用最新的穩定memcached版本(當前為memcached 3.1.3)。

由於PHP不支援memcache，因此必須安裝PHP的擴展才能使用它。 有兩個PHP擴展可用，對要使用的進行解碼非常重要：

- `memcache` (_沒有_) — 不定期維護的較舊但受歡迎的擴展。
的 `memcache` 當前擴展 _不_ 與7菲律賓比索一起工作。 請參閱 [memcache的PHP文檔](https://www.php.net/manual/en/book.memcache.php)。

   確切的名稱是 `php-pecl-memcache` CentOS。

- `memcached` (_帶`d`_) — 與PHP 7相容的更新且維護的擴展。 請參閱 [PHP Memcached文檔](https://www.php.net/manual/en/book.memcached.php)。

   確切的名稱是 `php-pecl-memcached` CentOS。

## 在CentOS上安裝和配置memcached

要在CentOS上安裝memcached，請以用戶身份執行以下任務 `root` 權限：

1. 安裝memcached及其依賴項：

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >前面命令的語法可能取決於您使用的程式包資料檔案庫。 例如，如果使用webtatic和PHP 5.6，請輸入 `yum install -y php56w-pecl-memcache`。 使用 `yum search memcache|grep php` 查找相應的包名稱。


1. 更改的memcached配置設定 `CACHESIZE` 和 `OPTIONS`:

   1. 開啟 `/etc/sysconfig/memcached` 的子菜單。
   1. 查找 `CACHESIZE` 將其更改為至少1 GB。 例如：

      ```config
      CACHESIZE="1GB"
      ```

   1. 查找 `OPTIONS` 並將其更改 `localhost` 或 `127.0.0.1`

1. 將更改保存到 `memcached` 並退出文本編輯器。
1. 重新啟動memcached。

   ```bash
   service memcached restart
   ```

1. 重新啟動Web伺服器。

   對於Apache:

   ```bash
   service httpd restart
   ```

1. 繼續下一節。

## 在安裝Commerce之前驗證memcached的工作

Adobe建議在安裝Commerce之前測試memcached以確保它工作。 這樣做只需幾分鐘，可以簡化以後的故障排除。

### 驗證Web伺服器是否識別memcached

要驗證Web伺服器是否識別Memcached:

1. 建立 `phpinfo.php` Web伺服器的docroot中的檔案：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在Web瀏覽器中轉到該頁面。

   例如， `http://192.0.2.1/phpinfo.php`

1. 確保memcache顯示如下：

![確認Web伺服器識別memcache](../../assets/configuration/memcache.png)

驗證您使用的是memcached 3.0.5版或更高版本。

如果memcache未顯示，請重新啟動Web伺服器並刷新瀏覽器頁。 如果仍未顯示，請驗證是否已安裝 `php-pecl-memcache` 擴展。

### 建立由MySQL資料庫和PHP指令碼組成的memcachetest

該test使用MySQL資料庫、表和資料來驗證您可以檢索資料庫資料並將其儲存在memcache中。 PHP指令碼首先搜索 [快取](https://glossary.magento.com/cache)。 如果結果不存在，則指令碼查詢資料庫。 在原始資料庫完成查詢後，指令碼將結果儲存在memcache中，使用 `set` 的子菜單。

[有關此test的詳細資訊](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

建立MySQL資料庫：

```bash
mysql -u root -p
```

在 `mysql` 提示符，輸入以下命令：

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

建立 `cache-test.php` 在Web伺服器的docroot中：

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

位置 `<memcached hostname or ip>` 或 `localhost`。 `127.0.0.1`，或memcache主機名或IP地址。 的 `<memcached port>` 是監聽埠；預設情況下， `11211`。

從命令行運行指令碼。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

第一個結果是 `got result from mysql`。 這表示密鑰在memcached中不存在，但是從MySQL中檢索的。

第二個結果是 `got result from memcached`，以驗證值是否成功儲存在memcached中。

最後，您可以使用Telnet查看memcache密鑰：

```bash
telnet localhost <memcache port>
```

在提示符下，輸入

```bash
stats items
```

結果與以下內容類似：

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

刷新記憶體快取並退出Telnet:

```bash
flush_all
```

```bash
quit
```

[有關Telnettest的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
