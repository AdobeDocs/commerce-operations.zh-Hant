---
title: 安全Cron PHP
description: 限制哪些人可以在瀏覽器中運行cron.php檔案。
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# 安全Cron PHP

本主題討論安全 `pub/cron.php` 防止其被惡意攻擊。 如果您不保護cron，則任何用戶都可能運行cron來攻擊您的Commerce應用程式。

cron作業運行多個計畫任務，是您的Commerce配置的重要部分。 計畫的任務包括但不限於：

- 重新索引
- 生成電子郵件
- 生成新聞稿
- 生成站點

>[!INFO]
>
>請參閱 [配置並運行cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 的子菜單。

您可以通過以下方式運行cron作業：

- 使用 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 命令，或在crontab中
- 訪問 `pub/cron.php?[group=<name>]` 在Web瀏覽器中

>[!INFO]
>
>如果你使用 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 命令以運行cron，因為它使用的進程已經安全。

## 使用Apache保護Cron

本節討論如何使用HTTP Basic身份驗證和Apache保護克隆。 這些說明基於Apache 2.2和CentOS 6。 有關詳細資訊，請參閱以下資源之一：

- [Apache 2.2身份驗證和授權教程](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4身份驗證和授權教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

### 建立密碼檔案

出於安全原因，您可以在Web伺服器域外的任何位置找到密碼檔案。 在此示例中，我們將密碼檔案儲存在新目錄中。

以用戶身份輸入以下命令 `root` 權限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

位置 `<username>` 可以是web伺服器用戶或其他用戶。 在本示例中，我們使用Web伺服器用戶，但用戶的選擇由您決定。

按照螢幕上的提示為用戶建立密碼。

要將其他用戶添加到密碼檔案中，請以用戶身份輸入以下命令 `root` 權限：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### 添加用戶以建立授權克隆組（可選）

通過將這些用戶添加到密碼檔案（包括組檔案）中，可以啟用多個用戶來運行cron。

將其他用戶添加到密碼檔案：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

要建立授權組，請在Web伺服器域外的任何位置建立組檔案。 組檔案指定組的名稱和組中的用戶。 在此示例中，組名稱為 `MagentoCronGroup`。

```bash
vim /usr/local/apache/password/group
```

檔案內容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### 安全Cron `.htaccess`

要保護Cron `.htaccess` 檔案：

1. 以檔案系統所有者身份或切換到檔案系統所有者身份登錄到Commerce伺服器。
1. 開啟 `<magento_root>/pub/.htaccess` 的子菜單。

   (因為 `cron.php` 位於 `pub` 目錄，編輯此 `.htaccess` 只有。)

1. _一個或多個用戶的Cron訪問。_ 替換現有 `<Files cron.php>` 指令，如下所示：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _組的Cron訪問。_ 替換現有 `<Files cron.php>` 指令，如下所示：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 將更改保存到 `.htaccess` 並退出文本編輯器。
1. 繼續 [驗證cron是否安全](#verify-cron-is-secure)。

## 使用Nginx保護Cron

本節討論如何使用Nginx Web伺服器保護克隆。 必須執行以下任務：

1. 為Nginx設定加密的密碼檔案
1. 在訪問時修改您的nginx配置以引用密碼檔案 `pub/cron.php`

### 建立密碼檔案

在繼續之前，請參考以下資源之一以建立密碼檔案：

- [如何在Ubuntu 14.04(DigitalOcean)上使用Nginx設定密碼驗證](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [使用Nginx(howtoforge)進行基本HTTP身份驗證](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### 安全Cron `nginx.conf.sample`

Commerce提供了現成的優化示例nginx配置檔案。 我們建議將其修改以保護cron。

1. 將以下內容添加到 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 檔案：

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

1.重新啟動nginx:

```bash
systemctl restart nginx
```

1. 繼續 [驗證cron是否安全](#verify-cron-is-secure)。

## 驗證cron是否安全

最簡單的方法來驗證 `pub/cron.php` 是安全的，即驗證它正在 `cron_schedule` 設定密碼驗證後的資料庫表。 此示例使用SQL命令檢查資料庫，但您可以使用任何您喜歡的工具。

>[!INFO]
>
>的 `default` 在此示例中運行的cron根據中定義的計畫運行 `crontab.xml`。 某些cron作業每天只運行一次。 首次從瀏覽器運行cron時， `cron_schedule` 表更新，但後續 `pub/cron.php` 請求按配置的計畫運行。

**驗證cron是否安全**:

1. 以Commerce資料庫用戶或以 `root`。

   比如說，

   ```bash
   mysql -u magento -p
   ```

1. 使用Commerce資料庫：

   ```shell
   use <database-name>;
   ```

   比如說，

   ```shell
   use magento;
   ```

1. 從 `cron_schedule` 資料庫表：

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. 從瀏覽器運行cron:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   例如：

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. 出現提示時，輸入授權用戶的名稱和密碼。 下圖顯示了一個示例。

   ![使用HTTP Basic授權克隆](../../assets/configuration/cron-auth.png)

1. 驗證是否將行添加到表：

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

## 從Web瀏覽器運行cron

您可以隨時使用Web瀏覽器運行cron。

>[!WARNING]
>
>做 _不_ 在瀏覽器中運行cron ，而不首先保護它。

如果使用的是Apache Web伺服器，則必須從 `.htaccess` 檔案，然後在瀏覽器中運行cron:

1. 以具有寫入Commerce檔案系統權限的用戶身份登錄到Commerce伺服器。
1. 在文本編輯器中開啟下列任一項(取決於Magento的入口點):

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. 刪除或注釋掉以下內容：

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   比如說，

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. 保存更改並退出文本編輯器。

   然後，您可以在Web瀏覽器中運行cron，如下所示：

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

位置：

- `<your hostname or IP>` 是Commerce安裝的主機名或IP地址
- `<Commerce root>` 是Commerce軟體所安裝的Web伺服器相對目錄

   您用於運行Commerce應用程式的確切URL取決於您如何配置Web伺服器和虛擬主機。

- `<group name>` 是任何有效的cron組名（可選）

比如說，

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>必須運行兩次cron:首先發現要運行的任務，然後再次發現任務本身。 請參閱 [配置並運行cron](../cli/configure-cron-jobs.md) 的子菜單。
