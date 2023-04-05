---
title: 設定遠程MySQL資料庫連接
description: 請依照下列步驟，為Adobe Commerce和Magento Open Source的內部部署安裝設定遠端資料庫連線。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# 設定遠程MySQL資料庫連接

有時，您可能希望將資料庫托管在單獨的伺服器上，而不是在同一台電腦上運行資料庫伺服器和Web伺服器。

Adobe提供了一種連接到不同電腦上的MySQL伺服器的方法。 自Adobe Commerce和Magento Open Source2.4.3版起，您也可以將應用程式設定為使用Amazon Web Services(AWS)Aurora資料庫，且不會變更程式碼。

Aurora是一種高效能、完全相容的MySQL Server，托管在AWS上。

## 連接到AWS Aurora資料庫

使用Aurora作為資料庫與使用預設資料庫連接器在常規Adobe Commerce和Magento Open Source設定配置中指定資料庫一樣簡單。

執行時 `bin/magento setup:install`，請在 `db-` 欄位：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

此 `db-host` 值是Aurora URL，具有 `https://` 和尾隨 `:portnumber`  移除。

## 設定遠程資料庫連接

>[!NOTE]
>
>這是一個高級主題，只應由經驗豐富的網路管理員或資料庫管理員使用。 您必須 `root` 訪問檔案系統，您必須能夠以 `root`.

### 必要條件

開始之前，您必須：

* [安裝MySQL Server](mysql.md) 在資料庫伺服器上。
* [建立資料庫實例](mysql.md#configuring-the-database-instance) 在資料庫伺服器上。
* 在Adobe Commerce或Magento Open SourceWeb節點上安裝MySQL客戶端。 有關詳細資訊，請參閱MySQL文檔。

### 高可用性

如果您的Web伺服器或資料庫伺服器已群集化，請使用以下准則配置遠程資料庫連接：

* 必須為每個Web伺服器節點配置連接。
* 通常，您會配置到資料庫負載平衡器的資料庫連接；但是，資料庫群集可能很複雜，配置取決於您。 Adobe沒有對資料庫群集提出具體建議。

   如需詳細資訊，請參閱 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 解決連線問題

如果連接到任一主機時出現問題，請先ping另一台主機，以確保該主機可以訪問。 您可能需要修改防火牆和SELinux規則（如果使用SELinux），以允許從一個主機到另一個主機的連接。

## 建立遠程連接

要建立遠程連接：

1. 在資料庫伺服器上，作為 `root` 權限，請開啟MySQL配置檔案。

   要定位，請輸入以下命令：

   ```bash
   mysql --help
   ```

   顯示的位置如下所示：

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >在Ubuntu 16上，通常是 `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 搜尋設定檔案 `bind-address`.

   如果存在，請依下列方式變更值。

   如果不存在，請將其新增至 `[mysqld]` 區段。

   ```conf
   bind-address = <ip address of your web node>
   ```

   請參閱 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)，尤其是如果您有叢集Web伺服器。

1. 將變更儲存至設定檔案，然後退出文字編輯器。
1. 重新啟動MySQL服務：

   * CentOS: `service mysqld restart`

   * 烏本圖： `service mysql restart`
   >[!NOTE]
   >
   >如果MySQL無法啟動，請在syslog中查找問題的源。 使用 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) 或其他權威來源。

## 授予資料庫用戶的訪問權限

要使Web節點能夠連接到資料庫伺服器，必須授予Web節點資料庫用戶對遠程伺服器上資料庫的訪問權限。

此範例授予 `root` 資料庫用戶完全訪問遠程主機上的資料庫。

要授予資料庫用戶的訪問權限：

1. 登錄到資料庫伺服器。
1. 連接到MySQL資料庫，作為 `root` 使用者。
1. 輸入以下命令：

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   例如，

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >如果Web伺服器已群集化，請在每個Web伺服器上輸入相同的命令。 必須對每個Web伺服器使用相同的用戶名。

## 驗證資料庫訪問

在Web節點主機上，輸入以下命令以驗證連接是否工作：

```bash
mysql -u <local database username> -h <database server ip address> -p
```

如果MySQL監視器顯示如下，則資料庫已準備好進行Adobe Commerce或Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

如果Web伺服器已群集化，請在每個Web伺服器主機上輸入命令。

## 安裝Adobe Commerce或Magento Open Source

安裝Adobe Commerce或Magento Open Source時，您必須指定下列項目：

* 基本URL(亦稱為 *儲存地址*)會指定的主機名或IP位址 *網站節點*
* 資料庫主機是 *遠程資料庫伺服器* IP地址（如果資料庫伺服器已群集，則為負載平衡器）
* 資料庫用戶名為 *本地Web節點* 授予訪問權限的資料庫用戶
* 資料庫密碼是本地Web節點用戶的密碼
* 資料庫名稱是遠程伺服器上資料庫的名稱
