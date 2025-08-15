---
title: 內部部署安裝必備條件
description: 深入瞭解Adobe Commerce內部部署安裝所需的軟體相依性。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# 內部部署安裝必備條件

安裝Adobe Commerce之前，您必須先執行下列動作：

* 設定一或多個符合[Commerce內部部署](../system-requirements.md)標籤中所列&#x200B;*系統需求*&#x200B;的主機。
* 如果您設定一個以上具有負載平衡的Web節點，請在安裝應用程式&#x200B;_之前設定並測試系統_&#x200B;的該部分。
* 請務必在安裝期間的各個時間點備份整個系統，以便在發生問題時將其回覆。

>[!NOTE]
>
>我們假設您是在&#x200B;**開發環境**&#x200B;中安裝Adobe Commerce，而且您擁有電腦&#x200B;**和**&#x200B;的根使用者存取權，因此電腦不需要高度安全。 如果您要設定較安全的機器，強烈建議您向網路管理員尋求其他協助。

我們強烈建議您更新並升級作業系統軟體。 這些升級可提供安全性與軟體修正，以防止未來發生問題。 不知道這代表什麼嗎？ 請檢視我們的[安裝概觀頁面](../overview.md)。

以具有`root`許可權的使用者身分輸入下列命令：

* 烏本圖

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

若要檢查您的系統是否有先決條件，請輸入下列命令：

### Apache

CentOS： `httpd -v`

Ubuntu： `apache2 -v`

Adobe Commerce支援Apache 2.4版，因為下列結果指出：

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

若要安裝或升級Apache，請參閱[Apache](web-server/apache.md)。

### PHP

請參閱&#x200B;*系統需求*&#x200B;中的[Commerce內部部署](../system-requirements.md)索引標籤，瞭解支援的PHP版本和[PHP](../system-requirements.md#php-settings)的PHP需求。

### MySQL

檢查您是否有相容的MySQL版本，適用於您正在安裝的Adobe Commerce版本。 如需支援的版本，請參閱&#x200B;*系統需求*&#x200B;中的[Commerce內部部署](../system-requirements.md)索引標籤。

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

下列結果表示您正在執行的版本。

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

輸入`help`或`\h`以取得說明。 鍵入`\c`以清除目前的輸入陳述式。

在`exit`提示下輸入`mysql>`以結束。

若要安裝或升級MySQL，請參閱[MySQL](database/mysql.md)。

### 搜尋引擎

驗證OpenSearch安裝：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

若要驗證Elasticsearch安裝：

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例如：

```bash
curl -XGET 'localhost:9200'
```

```
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
