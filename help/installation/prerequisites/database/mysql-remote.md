---
title: 設定遠程MySQL資料庫連接
description: 按照以下步驟配置遠程資料庫連接，以在Adobe Commerce和Magento Open Source的本地安裝。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# 設定遠程MySQL資料庫連接

有時，您可能希望將資料庫托管在單獨的伺服器上，而不是在同一台電腦上運行資料庫伺服器和Web伺服器。

Adobe提供了一種連接到不同電腦上的MySQL伺服器的方法。 從Adobe Commerce和Magento Open Source2.4.3開始，您還可以將應用程式配置為使用Amazon Web Services(AWS)Aurora資料庫，而不更改代碼。

Aurora是一種高效能、完全相容的MySQL伺服器，托管在AWS。

## 連接到AWSAurora資料庫

使用Aurora作為資料庫與使用預設資料庫連接器在常規Adobe Commerce和Magento Open Source設定配置中指定資料庫一樣簡單。

運行時 `bin/magento setup:install`，在 `db-` 欄位：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

的 `db-host` 值是帶有 `https://` 拖尾 `:portnumber`  已刪除。

## 設定遠程資料庫連接

>[!NOTE]
>
>這是一個高級主題，只應由經驗豐富的網路管理員或資料庫管理員使用。 你一定有 `root` 訪問檔案系統，您必須能夠以 `root`。

### 先決條件

在開始之前，您必須：

* [安裝MySQL Server](mysql.md) 在資料庫伺服器上。
* [建立資料庫實例](mysql.md#configuring-the-database-instance) 在資料庫伺服器上。
* 在您的Adobe Commerce或Magento Open SourceWeb節點上安裝MySQL客戶端。 有關詳細資訊，請參閱MySQL文檔。

### 高可用性

如果Web伺服器或資料庫伺服器是群集的，請使用以下指導配置遠程資料庫連接：

* 必須為每個Web伺服器節點配置連接。
* 通常，您配置到資料庫負載平衡器的資料庫連接；但是，資料庫群集可能很複雜，配置取決於您。 Adobe沒有為資料庫群集提出具體建議。

   有關詳細資訊，請參見 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html)。

### 解決連接問題

如果連接到任一主機時出現問題，請首先ping另一主機以確保其可訪問。 您可能需要通過修改防火牆和SELinux規則（如果使用SELinux）來允許從一台主機到另一台主機的連接。

## 建立遠程連接

要建立遠程連接：

1. 在資料庫伺服器上，作為 `root` 權限，開啟MySQL配置檔案。

   要找到它，請輸入以下命令：

   ```bash
   mysql --help
   ```

   該位置顯示與以下內容類似：

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >在Ubuntu 16上，通常 `/etc/mysql/mysql.conf.d/mysqld.cnf`。

1. 搜索配置檔案 `bind-address`。

   如果存在，請按如下方式更改值。

   如果它不存在，請將其添加到 `[mysqld]` 的子菜單。

   ```conf
   bind-address = <ip address of your web node>
   ```

   請參閱 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)，尤其是如果您有群集Web伺服器。

1. 將更改保存到配置檔案並退出文本編輯器。
1. 重新啟動MySQL服務：

   * CentOS: `service mysqld restart`

   * 烏班圖： `service mysql restart`
   >[!NOTE]
   >
   >如果MySQL無法啟動，請在syslog中查找問題的源。 使用 [MySQL文檔](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) 或其他權威來源。

## 授予對資料庫用戶的訪問權限

要使Web節點能夠連接到資料庫伺服器，必須授予Web節點資料庫用戶對遠程伺服器上資料庫的訪問權限。

此示例將授予 `root` 資料庫用戶對遠程主機上的資料庫具有完全訪問權限。

要授予對資料庫用戶的訪問權限：

1. 登錄到資料庫伺服器。
1. 以 `root` 。
1. 輸入以下命令：

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   比如說，

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >如果Web伺服器是群集的，請在每個Web伺服器上輸入相同的命令。 必須為每個Web伺服器使用相同的用戶名。

## 驗證資料庫訪問

在Web節點主機上，輸入以下命令以驗證連接是否正常：

```bash
mysql -u <local database username> -h <database server ip address> -p
```

如果MySQL監視器顯示如下，則資料庫已準備好用於Adobe Commerce或Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

如果Web伺服器是群集的，請在每個Web伺服器主機上輸入該命令。

## 安裝Adobe Commerce或Magento Open Source

安裝Adobe Commerce或Magento Open Source時，必須指定以下內容：

* 基本URL(也稱為 *儲存地址*)指定的主機名或IP地址 *Web節點*
* 資料庫主機是 *遠程資料庫伺服器* IP地址（或者，如果資料庫伺服器是群集的，則負載平衡器）
* 資料庫用戶名是 *本地Web節點* 授予訪問權限的資料庫用戶
* 資料庫密碼是本地Web節點用戶的密碼
* 資料庫名稱是遠程伺服器上資料庫的名稱
