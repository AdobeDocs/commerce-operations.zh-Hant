---
title: 搜索引擎先決條件
description: 按照以下步驟安裝和配置支援的搜索引擎軟體，以在Adobe Commerce和Magento Open Source的內部安裝。
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# 搜索引擎先決條件

自Adobe Commerce和Magento Open Source2.4起，所有安裝都必須配置為使用 [Elasticsearch](https://www.elastic.co) 或 [開啟搜索](https://opensearch.org/) 作為目錄搜索解決方案。

>[!NOTE]
>
>已在2.4.4中添加了OpenSearch支援。OpenSearch是相容的Elasticsearch分叉。 配置Elasticsearch7的所有說明都適用於OpenSearch。 [從Elasticsearch遷移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 提供了切換到OpenSearch的指導。

## 支援的版本

安裝Adobe Commerce2.4.4及更高版本之前，必須安裝並配置Elasticsearch或OpenSearch。

請參閱 [系統要求](../../system-requirements.md) 的子菜單。

## 建議的配置

我們建議：

* [為搜索引擎配置nginx](configure-nginx.md)
* [為搜索引擎配置Apache](configure-apache.md)

## 安裝位置

以下任務假定您已根據以下圖表配置系統：

![搜索引擎圖](../../../assets/installation/search-engine-config.svg)

上圖顯示：

* Commerce應用程式和搜索引擎安裝在不同的主機上。

   在單獨的主機上運行需要代理才能工作。 (對搜索引擎進行聚類超出本指南的範圍，但您可以在 [Elasticsearch群集文檔](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html)。)

* 每台主機都有自己的Web伺服器；Web伺服器不必是相同的。

   例如，Commerce應用程式可以運行Apache，而搜索引擎可以運行nginx。

* 兩個Web伺服器都使用傳輸層安全性(TLS)。

   設定TLS超出了我們文檔的範圍。

按如下方式處理搜索請求：

1. Commerce Web伺服器接收來自用戶的搜索請求，該伺服器將其轉發到搜索引擎伺服器。

   將搜索引擎配置為連接到代理的主機和埠。 我們建議使用Web伺服器的SSL埠（預設為443）。

1. 搜索引擎Web伺服器（偵聽埠443）將請求代理到搜索引擎伺服器（預設情況下，它偵聽埠9200）。

1. HTTP Basic驗證進一步保護了對搜索引擎的訪問。 要請求訪問搜索引擎，它必須通過SSL傳輸 *和* 提供有效的用戶名和密碼。

1. 搜索引擎處理該請求。

1. 通信沿同一路由返回，ElasticsearchWeb伺服器充當安全反向代理。

## 先決條件

本節中討論的任務要求：

* [防火牆和SELinux](#firewall-and-selinux)
* [安裝Java軟體開發工具包(JDK)](#install-the-java-software-development-kit)
* [安裝搜索引擎](#install-the-search-engine)
* [升級Elasticsearch](#upgrading-elasticsearch)

### 防火牆和SELinux

預設情況下，可以配置與安全相關的軟體(iptables、SELinux、AppArmor)，以阻止子系統之間的通信。 如果有問題，不妨檢查一下。

#### 設定iptables和SELinux的規則

要設定允許與啟用防火牆或SELinux通信的規則，請參考以下資源：

* [iptableshow to](https://help.ubuntu.com/community/IptablesHowTo)
* [如何編輯Iptables規則（fedora項目）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux(CentOS.org)簡介](https://www.centos.org)
* [SELinux How-To Wiki(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### 安裝Java軟體開發工具包

要確定是否已安裝Java，請輸入以下命令：

```bash
java -version
```

如果消息 `java: command not found` 顯示，必須按照下一節中討論的方式安裝Java SDK。

請參閱以下部分之一：

* [在CentOS上安裝最新的JDK](#install-the-jdk-on-centos)
* [在Ubuntu上安裝最新的JDK](#install-the-jdk-on-ubuntu)

#### 在CentOS上安裝JDK

查看 [數字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8)。

確保安裝JDK和 *不* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java版本8可能不適用於所有作業系統。 例如， [搜索Ubuntu的可用包清單](https://packages.ubuntu.com/)。

#### 在Ubuntu上安裝JDK

要在Ubuntu上安裝JDK 1.8，請以用戶身份輸入以下命令 `root` 權限：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

有關其他選項，請參見 [Oracle文檔](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html)。

### 安裝搜索引擎

關注 [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 或 [安裝和配置OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) 針對特定平台的步驟。

要驗證Elasticsearch是否正在工作，請在運行該命令的伺服器上輸入以下命令：

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

將顯示一條類似以下內容的消息：

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

要驗證OpenSearch是否正在工作，請輸入以下命令：

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## 升級Elasticsearch

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關備份資料、檢測潛在遷移問題和在部署到生產之前測試升級的完整說明。 根據您當前版本的Elasticsearch，可能需要或不需要完全群集重新啟動。

Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發工具包](#install-the-java-software-development-kit) 以檢查安裝的JDK版本。

## 其他資源

查看 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 或 [開啟搜索](https://opensearch.org/docs/latest/) 文檔。
