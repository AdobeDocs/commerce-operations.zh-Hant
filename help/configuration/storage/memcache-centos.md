---
title: 在CentOS上設定memcached
description: 在CentOS上安裝和配置memcached。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# 在CentOS上設定memcached

本節提供在CentOS上安裝MemcAched的說明。 如需詳細資訊，請參閱 [梅卡達維基](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe建議使用最新的穩定memcached版本（目前memcached為3.1.3）。

由於PHP不支援memcache，因此您必須安裝PHP的擴展才能使用它。 有兩個PHP擴充功能可供使用，請務必將要使用的擴充功能解碼：

- `memcache` (_no d_) — 較舊但受歡迎的擴充功能，不會定期維護。
此 `memcache` 目前擴充功能 _不_ 與PHP 7搭配使用。 請參閱 [門快取的PHP文檔](https://www.php.net/manual/en/book.memcache.php).

   確切名稱為 `php-pecl-memcache` 用於CentOS。

- `memcached` (_帶`d`_) — 與PHP 7相容的較新且維護的擴充功能。 請參閱 [memcached的PHP文檔](https://www.php.net/manual/en/book.memcached.php).

   確切名稱為 `php-pecl-memcached` 用於CentOS。

## 在CentOS上安裝和配置memcached

要在CentOS上安裝Memcached，請以用戶身份執行以下任務 `root` 權限：

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
   >前面命令的語法可能取決於您使用的程式包儲存庫。 例如，如果您使用WebTatic和PHP 5.6，請輸入 `yum install -y php56w-pecl-memcache`. 使用 `yum search memcache|grep php` 來查找相應的包名。


1. 更改的memcached配置設定 `CACHESIZE` 和 `OPTIONS`:

   1. 開啟 `/etc/sysconfig/memcached` 在文字編輯器中。
   1. 找出 `CACHESIZE` 並將其更改為至少1 GB。 例如：

      ```config
      CACHESIZE="1GB"
      ```

   1. 找出 `OPTIONS` 並將 `localhost` 或 `127.0.0.1`

1. 將變更儲存至 `memcached` 並退出文字編輯器。
1. 重新啟動memcached。

   ```bash
   service memcached restart
   ```

1. 重新啟動Web伺服器。

   Apache:

   ```bash
   service httpd restart
   ```

1. 繼續下一節。

## 安裝Commerce之前驗證Memcached工作

Adobe建議先測試memcached，以在您安裝商務前確定它有效。 這麼做只需幾分鐘的時間，日後可簡化疑難排解。

### 驗證Web伺服器是否識別mmcached

要驗證Web伺服器是否識別了memcached:

1. 建立 `phpinfo.php` 檔案（位於Web伺服器的docroot中）:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在網頁瀏覽器中前往該頁面。

   例如， `http://192.0.2.1/phpinfo.php`

1. 確保memcache顯示如下：

![確認Web伺服器已識別記憶體快取](../../assets/configuration/memcache.png)

確認您使用的是memcached 3.0.5版或更新版本。

如果未顯示memcache，請重新啟動Web伺服器並刷新瀏覽器頁。 如果仍未顯示，請確認您已安裝 `php-pecl-memcache` 擴充功能。

### 建立由MySQL資料庫和PHP指令碼組成的memcache測試

測試使用MySQL資料庫、表和資料來驗證您可以檢索資料庫資料並將其儲存在memcache中。 PHP指令碼首先搜索快取。 如果結果不存在，則指令碼將查詢資料庫。 在原始資料庫完成查詢後，指令碼將結果儲存在memcache中，使用 `set` 命令。

[有關此測試的更多詳細資訊](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

建立MySQL資料庫：

```bash
mysql -u root -p
```

在 `mysql` 提示，輸入以下命令：

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

其中 `<memcached hostname or ip>` 為 `localhost`, `127.0.0.1`，或memcache主機名或IP地址。 此 `<memcached port>` 是監聽埠；依預設， `11211`.

從命令列執行指令碼。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

第一個結果是 `got result from mysql`. 這表示密鑰不存在於memcached中，但是從MySQL中檢索到的。

第二個結果是 `got result from memcached`，可驗證值是否在memcached中成功儲存。

最後，您可以使用Telnet查看記憶體快取密鑰：

```bash
telnet localhost <memcache port>
```

在提示符下，輸入

```bash
stats items
```

結果類似下列：

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

刷新記憶體快取儲存並退出Telnet:

```bash
flush_all
```

```bash
quit
```

[有關Telnet測試的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
