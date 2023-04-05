---
title: 搜尋引擎必要條件
description: 請依照下列步驟，安裝並設定支援的搜尋引擎軟體，以安裝Adobe Commerce和Magento Open Source的內部部署。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# 搜尋引擎必要條件

自Adobe Commerce和Magento Open Source2.4起，所有安裝都必須設定為使用 [Elasticsearch](https://www.elastic.co) 或 [OpenSearch](https://opensearch.org/) 作為目錄搜尋解決方案。

>[!NOTE]
>
>2.4.4中新增了OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 配置Elasticsearch7的所有說明均適用於OpenSearch。 [從Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 提供切換至OpenSearch的指引。

## 支援的版本

安裝Adobe Commerce 2.4.4和更新版本之前，您必須先安裝並設定Elasticsearch或OpenSearch。

請參閱 [系統需求](../../system-requirements.md) 以取得特定版本資訊。

## 建議的設定

我們建議下列項目：

* [為搜尋引擎設定nginx](configure-nginx.md)
* [為您的搜尋引擎設定Apache](configure-apache.md)

## 安裝位置

以下任務假定您已根據下圖配置了系統：

![搜尋引擎圖表](../../../assets/installation/search-engine-config.svg)

上圖顯示：

* 商務應用程式和搜尋引擎安裝在不同的主機上。

   在個別主機上執行需要代理才能運作。 (將搜尋引擎聚類超出本指南的範圍，但您可在 [Elasticsearch聚類文檔](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* 每個主機都有自己的Web伺服器；web伺服器不必相同。

   例如，商務應用程式可以執行Apache，而搜尋引擎可以執行nginx。

* 兩台Web伺服器均使用傳輸層安全性(TLS)。

   設定TLS不在本檔案的討論範圍內。

處理搜尋請求的方式如下：

1. 商務Web伺服器接收來自用戶的搜索請求，該伺服器將其轉發到搜索引擎伺服器。

   您可以設定搜尋引擎以連線至代理的主機和連接埠。 建議使用Web伺服器的SSL埠（預設為443）。

1. 搜索引擎Web伺服器（在埠443上偵聽）將請求代理到搜索引擎伺服器（預設情況下，它在埠9200上偵聽）。

1. HTTP Basic驗證可進一步保護搜尋引擎的存取權。 若要要求連線至搜尋引擎，必須透過SSL傳送 *和* 提供有效的用戶名和密碼。

1. 搜尋引擎會處理請求。

1. 通信會沿同一路由返回，ElasticsearchWeb伺服器充當安全反向代理。

## 必要條件

本節中討論的任務需要：

* [防火牆和SELinux](#firewall-and-selinux)
* [安裝Java軟體開發套件(JDK)](#install-the-java-software-development-kit)
* [安裝搜尋引擎](#install-the-search-engine)
* [升級Elasticsearch](#upgrading-elasticsearch)

### 防火牆和SELinux

預設情況下，與安全相關的軟體(iptables、SELinux、AppArmor)可以配置為阻止子系統之間的通信。 如果有問題，檢查它們或許是個好主意。

#### 為iptables和SELinux設定規則

要設定允許與已啟用防火牆或SELinux的通信的規則，請查閱以下資源：

* [iptables操作說明](https://help.ubuntu.com/community/IptablesHowTo)
* [如何編輯iptables規則（fedora專案）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux簡介(CentOS.org)](https://www.centos.org)
* [SELinux How-To Wiki(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### 安裝Java軟體開發套件

要確定是否已安裝Java，請輸入以下命令：

```bash
java -version
```

如果訊息 `java: command not found` 顯示時，您必須依照下一節所述安裝Java SDK。

請參閱下列其中一節：

* [在CentOS上安裝最新的JDK](#install-the-jdk-on-centos)
* [在Ubuntu上安裝最新的JDK](#install-the-jdk-on-ubuntu)

#### 在CentOS上安裝JDK

看這個 [數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

請務必安裝JDK和 *not* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java版本8可能不適用於所有作業系統。 例如，您可以 [搜索Ubuntu的可用包清單](https://packages.ubuntu.com/).

#### 在Ubuntu上安裝JDK

要在Ubuntu上安裝JDK 1.8，請以用戶身份輸入以下命令 `root` 權限：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

如需其他選項，請參閱 [Oracle檔案](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 安裝搜尋引擎

追隨 [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 或 [安裝和配置OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) 以取得平台專屬步驟。

要驗證Elasticsearch是否正常運行，請在運行該伺服器的伺服器上輸入以下命令：

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

畫面上會顯示類似下列的訊息：

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

要驗證OpenSearch是否正常工作，請輸入以下命令：

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## 升級Elasticsearch

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關在部署到生產環境之前備份資料、檢測潛在遷移問題和測試升級的完整說明。 視您當前的Elasticsearch版本而定，可能需要或不需要完全群集重新啟動。

Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發套件](#install-the-java-software-development-kit) 來檢查安裝的JDK版本。

## 其他資源

請參閱 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 或 [OpenSearch](https://opensearch.org/docs/latest/) 檔案。
