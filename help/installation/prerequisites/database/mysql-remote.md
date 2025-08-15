---
title: 設定遠端MySQL資料庫連線
description: 請依照下列步驟，為Adobe Commerce的內部安裝設定遠端資料庫連線。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# 設定遠端MySQL資料庫連線

有時候，您可能會想要將資料庫託管在不同伺服器上，而不是在同一部電腦上執行資料庫伺服器和網頁伺服器。

Adobe已提供一種連線至其他電腦上的MySQL伺服器的方式。 自Adobe Commerce 2.4.3起，您也可以將應用程式設定為使用Amazon Web Services (AWS) Aurora資料庫，而不變更程式碼。

Aurora是高效能、完全相容的MySQL伺服器，裝載於AWS上。

## 連線到AWS Aurora資料庫

使用Aurora做為資料庫，就像使用預設的資料庫聯結器，在一般Adobe Commerce安裝組態中指定資料庫一樣容易。

執行`bin/magento setup:install`時，請使用`db-`欄位中的Aurora資訊：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

`db-host`值是已移除`https://`及尾端`:portnumber`的Aurora URL。

## 設定遠端資料庫連線

>[!NOTE]
>
>這是進階主題，僅供經驗豐富的網路管理員或資料庫管理員使用。 您必須具有`root`檔案系統存取權，而且必須能夠以`root`身分登入MySQL。

### 先決條件

開始之前，您必須：

* [在資料庫伺服器上安裝MySQL伺服器](mysql.md)。
* [在資料庫伺服器上建立資料庫執行個體](mysql.md#configuring-the-database-instance)。
* 在您的Adobe Commerce Web節點上安裝MySQL使用者端。 如需詳細資訊，請參閱MySQL檔案。

### 高可用性

如果您的Web伺服器或資料庫伺服器是叢集化的，請使用下列准則來設定遠端資料庫連線：

* 您必須為每個Web伺服器節點設定連線。
* 一般而言，您會設定資料庫連線到資料庫負載平衡器；不過，資料庫叢集可能很複雜，其設定取決於您。 Adobe未針對資料庫叢集提出特定建議。

  如需詳細資訊，請參閱[MySQL檔案](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html)。

### 解決連線問題

如果您無法連線到任一主機，請先偵測另一台主機，確定可以連線。 您可能需要修改防火牆和SELinux規則（如果使用SELinux），以允許主機之間的連線。

## 建立遠端連線

若要建立遠端連線：

1. 在您的資料庫伺服器上，以具有`root`許可權的使用者身分，開啟您的MySQL設定檔。

   若要尋找它，請輸入下列命令：

   ```bash
   mysql --help
   ```

   位置顯示方式與以下類似：

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >在Ubuntu 16上，路徑通常是`/etc/mysql/mysql.conf.d/mysqld.cnf`。

1. 搜尋`bind-address`的組態檔。

   如果值存在，請依下列方式變更值。

   如果不存在，則將其新增到`[mysqld]`區段。

   ```conf
   bind-address = <ip address of your web node>
   ```

   請參閱[MySQL檔案](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)，尤其是如果您有叢集化網頁伺服器。

1. 將變更儲存至組態檔並退出文字編輯器。
1. 重新啟動MySQL服務：

   * CentOS： `service mysqld restart`

   * Ubuntu： `service mysql restart`

   >[!NOTE]
   >
   >如果MySQL無法啟動，請在syslog中尋找問題的來源。 使用[MySQL檔案](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address)或其他授權來源來解決問題。

## 授與資料庫使用者的存取權

若要讓Web節點連線到資料庫伺服器，您必須授予Web節點資料庫使用者對遠端伺服器上資料庫的存取權。

此範例授予`root`資料庫使用者對遠端主機上資料庫的完整存取權。

若要將存取權授與資料庫使用者：

1. 登入資料庫伺服器。
1. 以`root`使用者身分連線至MySQL資料庫。
1. 輸入下列命令：

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   例如，

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >如果您的網頁伺服器是叢集化的，請在每個網頁伺服器上輸入相同的命令。 每個網頁伺服器必須使用相同的使用者名稱。

## 驗證資料庫存取權

在您的Web節點主機上，輸入下列命令來驗證連線是否有效：

```bash
mysql -u <local database username> -h <database server ip address> -p
```

如果MySQL監視器顯示如下，表示資料庫已準備好使用Adobe Commerce：

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

如果您的Web伺服器是叢集化的，請在每個Web伺服器主機上輸入命令。

## 安裝Adobe Commerce

安裝Adobe Commerce時，您必須指定下列專案：

* 基底URL （也稱為&#x200B;*存放區位址*）指定&#x200B;*網頁節點*&#x200B;的主機名稱或IP位址
* 資料庫主機是&#x200B;*遠端資料庫伺服器* IP位址（如果資料庫伺服器是叢集化的，則為負載平衡器）
* 資料庫使用者名稱是您授與存取權的&#x200B;*本機Web節點*&#x200B;資料庫使用者
* 資料庫密碼是本機Web節點使用者的密碼
* 資料庫名稱是遠端伺服器上的資料庫名稱
