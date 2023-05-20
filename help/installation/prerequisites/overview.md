---
title: 本地安裝先決條件
description: 瞭解有關Adobe Commerce和Magento Open Source內部安裝所需軟體依賴項的詳細資訊。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 本地安裝先決條件

在安裝Adobe Commerce或Magento Open Source之前，必須執行以下操作：

* 設定一個或多個滿足以下條件的主機 [系統要求](../system-requirements.md)。
* 如果要設定多個具有負載平衡的Web節點，請設定並test系統的該部分 _先_ 安裝應用程式。
* 確保在安裝過程中可以在不同點備份整個系統，以便在出現問題時可以回滾。

>[!NOTE]
>
>我們假設你將Adobe Commerce或Magento Open Source **開發環境**，您擁有對電腦的根用戶訪問權限， **和** 機器不需要高度安全。 如果您正在設定更安全的電腦，強烈建議您咨詢網路管理員以獲得其他幫助。

強烈建議您更新和升級作業系統軟體。 這些升級可提供安全和軟體修復，從而防止將來出現問題。 不知道這意味著什麼？ 看看我們 [安裝概述頁](../overview.md)。

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

要檢查系統的先決條件，請輸入以下命令：

### 阿帕奇

CentOS: `httpd -v`

烏班圖： `apache2 -v`

Adobe Commerce和Magento Open Source支援Apache 2.4版，如下結果所示：

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

要安裝或升級Apache，請參見 [阿帕奇](web-server/apache.md)。

### 菲律賓比索

請參閱 [系統要求](../system-requirements.md) 支援的PHP和 [菲律賓比索] 滿足PHP要求。

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

檢查您是否有正確的MySQL版本，以瞭解您正在安裝的Adobe Commerce或Magento Open Source([在此處檢查支援的版本](../system-requirements.md)。 以下結果表示您正在運行的版本。)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

類型 `help` 或 `\h` 的雙曲餘切值。 類型 `\c` 以清除當前輸入語句。

輸入 `exit` 的 `mysql>` 提示退出。

要安裝或升級MySQL，請參見 [MySQL](database/mysql.md)。

### 搜索引擎

要驗證OpenSearch安裝：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

要驗證Elasticsearch安裝：

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
