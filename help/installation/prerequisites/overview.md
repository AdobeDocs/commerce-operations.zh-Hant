---
title: 本地安裝必備條件
description: 進一步了解Adobe Commerce和Magento Open Source的內部部署安裝所需的軟體相依性。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---


# 本地安裝必備條件

安裝Adobe Commerce或Magento Open Source之前，您必須先執行下列操作：

* 設定符合以下條件的一或多個主機 [系統需求](../system-requirements.md).
* 如果您要設定多個具有負載平衡的Web節點，請設定並測試系統的該部分 _befor_ 安裝應用程式。
* 請務必在安裝過程中的各個時間點備份整個系統，以便在出現問題時可以回滾。

>[!NOTE]
>
>假設您要在 **開發環境**，即您擁有電腦的根使用者存取權， **和** 機器不需要高度安全。 如果要設定更安全的電腦，強烈建議您向網路管理員尋求其他幫助。

強烈建議您更新和升級作業系統軟體。 這些升級可以提供安全性和軟體修復，以防止將來出現問題。 不知道這意味著什麼？ 看看我們的 [安裝概述頁面](../overview.md).

以用戶身份輸入以下命令 `root` 權限：

* 烏邦圖

   ```bash
   apt-get update
   ```

   ```bash
   apt-get upgrade
   ```

* CentOS

   ```bash
   yum -y update
   ```

   ```bash
   yum -y upgrade
   ```

## 先決條件檢查

要檢查系統是否有必要條件，請輸入以下命令：

### Apache

CentOS: `httpd -v`

烏本圖： `apache2 -v`

Adobe Commerce和Magento Open Source支援Apache 2.4版，如下結果所示：

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

若要安裝或升級Apache，請參閱 [Apache](web-server/apache.md).

### PHP

請參閱 [系統需求](../system-requirements.md) 支援版本的PHP和 [PHP] PHP要求。

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

檢查您是否有正確版本的Adobe Commerce或正在安裝的Magento Open Source([查看這裡以了解支援的版本](../system-requirements.md). 下列結果表示您執行的版本。)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

類型 `help` 或 `\h` 來幫忙。 類型 `\c` 來清除當前輸入語句。

輸入 `exit` at `mysql>` 提示退出。

要安裝或升級MySQL，請參見 [MySQL](database/mysql.md).

### Elasticsearch或OpenSearch

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例如：

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
