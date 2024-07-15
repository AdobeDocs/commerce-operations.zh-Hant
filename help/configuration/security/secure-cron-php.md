---
title: 安全cron PHP
description: 限制誰能在瀏覽器中執行cron.php檔案。
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# 安全cron PHP

本主題討論如何保護`pub/cron.php`，以防止其被惡意利用。 如果您不保護cron的安全，任何使用者都可能執行cron來攻擊您的Commerce應用程式。

cron工作會執行數個排程工作，是Commerce設定的重要一環。 已排程的工作包括但不限於：

- 重新索引
- 產生電子郵件
- 產生電子報
- 產生網站地圖

>[!INFO]
>
>如需有關cron群組的詳細資訊，請參閱[設定並執行cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)。

您可以透過下列方式執行cron工作：

- 從命令列或在crontab中使用[`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)命令
- 在網頁瀏覽器中存取`pub/cron.php?[group=<name>]`

>[!INFO]
>
>如果您使用[`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)命令來執行cron，則不需要執行任何動作，因為它使用已經安全的不同處理序。

## 使用Apache的安全CRON

本節將討論如何透過Apache使用HTTP基本驗證來保護Cron安全。 這些指示是根據具有CentOS 6的Apache 2.2。 如需詳細資訊，請參閱下列資源之一：

- [Apache 2.2驗證和授權教學課程](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4驗證和授權教學課程](https://httpd.apache.org/docs/2.4/howto/auth.html)

### 建立密碼檔案

基於安全考量，您可以在網頁伺服器docroot以外的任何地方找到密碼檔案。 在此範例中，我們將密碼檔案儲存在新目錄中。

以具有`root`許可權的使用者身分輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

其中`<username>`可以是網頁伺服器使用者或其他使用者。 在此範例中，我們使用Web伺服器使用者，但使用者的選擇由您決定。

按照畫面上的提示為使用者建立密碼。

若要將其他使用者新增至您的密碼檔案，請以具有`root`許可權的使用者身分輸入下列命令：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### 新增使用者以建立授權的cron群組（選用）

您可以將這些使用者新增到您的密碼檔案（包括群組檔案），讓多個使用者執行cron。

若要將其他使用者新增至您的密碼檔案：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

若要建立授權群組，請在網頁伺服器docroot之外的任意位置建立群組檔案。 群組檔案指定群組的名稱以及群組中的使用者。 在此範例中，群組名稱為`MagentoCronGroup`。

```bash
vim /usr/local/apache/password/group
```

檔案內容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### `.htaccess`中的安全Cron

若要保護`.htaccess`檔案中的cron安全：

1. 以檔案系統擁有者的身分登入或切換到您的Commerce伺服器。
1. 在文字編輯器中開啟`<magento_root>/pub/.htaccess`。

   （由於`cron.php`位於`pub`目錄中，請僅編輯此`.htaccess`。）

1. 一個或多個使用者的&#x200B;_Cron存取權。_&#x200B;將現有的`<Files cron.php>`指示詞取代為：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. 群組&#x200B;_Cron存取權。_&#x200B;將現有的`<Files cron.php>`指示詞取代為：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 將變更儲存至`.htaccess`並結束文字編輯器。
1. 繼續使用[驗證cron是否安全](#verify-cron-is-secure)。

## 使用Nginx提供安全的cron

本節討論如何使用Nginx網頁伺服器來保護cron的安全。 您必須執行下列工作：

1. 設定Nginx的加密密碼檔案
1. 修改您的nginx組態以在存取`pub/cron.php`時參考密碼檔案

### 建立密碼檔案

在繼續之前，請查詢下列資源之一以建立密碼檔案：

- [如何在Ubuntu 14.04 (DigitalOcean)上設定Nginx的密碼驗證](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [使用Nginx進行基本HTTP驗證(howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### `nginx.conf.sample`中的安全Cron

Commerce提供立即可用的最佳化nginx設定檔範例。 我們建議您修改它以保護cron。

1. 將下列專案新增至您的[`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)檔案：

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.重新啟動nginx：

```bash
systemctl restart nginx
```

1. 繼續使用[驗證cron是否安全](#verify-cron-is-secure)。

## 驗證cron是否安全

驗證`pub/cron.php`是否安全的最簡單方法是在您設定密碼驗證後，驗證它是否在`cron_schedule`資料庫表格中建立資料列。 此範例使用SQL命令來檢查資料庫，但您可以使用任何您喜歡的工具。

>[!INFO]
>
>您在此範例中執行的`default` cron會根據`crontab.xml`中定義的排程執行。 某些cron工作一天只執行一次。 第一次從瀏覽器執行cron時，`cron_schedule`資料表會更新，但後續的`pub/cron.php`要求會依設定的排程執行。

**驗證cron是否安全**：

1. 以Commerce資料庫使用者或`root`身分登入資料庫。

   例如，

   ```bash
   mysql -u magento -p
   ```

1. 使用Commerce資料庫：

   ```shell
   use <database-name>;
   ```

   例如，

   ```shell
   use magento;
   ```

1. 刪除`cron_schedule`資料庫資料表中的所有資料列：

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. 從瀏覽器執行cron：

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   例如：

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. 出現提示時，輸入授權使用者的名稱和密碼。 下圖顯示一個範例。

   ![使用HTTP Basic授權cron](../../assets/configuration/cron-auth.png)

1. 確認資料列已新增至表格：

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## 從網頁瀏覽器執行cron

您可以隨時使用網頁瀏覽器執行cron，例如在開發期間。

>[!WARNING]
>
>請&#x200B;_不要_&#x200B;在瀏覽器中執行cron，而不先保護它。

如果您使用Apache網頁伺服器，必須先從`.htaccess`檔案移除限制，才能在瀏覽器中執行cron：

1. 以具有寫入Commerce檔案系統許可權的使用者身分登入您的Commerce伺服器。
1. 在文字編輯器中開啟下列任一專案(視您的Magento進入點而定)：

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. 刪除或註解下列專案：

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   例如，

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. 儲存變更並退出文字編輯器。

   然後您可以在網頁瀏覽器中執行cron，如下所示：

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

其中：

- `<your hostname or IP>`是Commerce安裝的主機名稱或IP位址
- `<Commerce root>`是您安裝Commerce軟體的網頁伺服器docroot相對目錄

  您用來執行Commerce應用程式的確切URL取決於您設定Web伺服器和虛擬主機的方式。

- `<group name>`是任何有效的cron群組名稱（選擇性）

例如，

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>您必須執行兩次cron：首先要發現要執行的任務，然後再次執行任務本身。 如需有關cron群組的詳細資訊，請參閱[設定並執行cron](../cli/configure-cron-jobs.md)。
