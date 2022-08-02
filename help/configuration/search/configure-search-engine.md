---
title: 搜索引擎配置
description: 配置具有Adobe Commerce和Magento Open Source的搜索引擎。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# 搜索引擎配置

本節討論必須選擇的testElasticsearch或OpenSearch與Adobe Commerce和Magento Open Source的最小設定。 截至2.4.4和2.4.3-p2版，所有欄位都標有 **Elasticsearch** 也適用於OpenSearch。

有關配置搜索引擎的其他詳細資訊，請參閱 [使用手冊](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html)。

## 從管理員配置您的搜索引擎

要將系統配置為使用Elasticsearch或OpenSearch，請執行以下操作：

1. 以管理員身份登錄到管理員。
1. 按一下 **商店** >設定> **配置** > **目錄** > **目錄** > **目錄搜索**。
1. 從 **搜索引擎** 清單中，選擇搜索引擎的相應版本。如果使用OpenSearch，則必須選擇Elasticsearch7。

   下表列出了配置和test與Commerce的連接所需的配置選項。
除非您更改了搜索引擎的伺服器設定，否則預設值應有效。 跳至下一步。

   | 選項 | 說明 |
   |--- |--- |
   | **Elasticsearch伺服器主機名** | 輸入運行Elasticsearch或OpenSearch的電腦的完全限定主機名或IP地址。<br>Adobe Commerce在雲基礎架構方面：從整合系統中獲取此值。 |
   | **Elasticsearch伺服器埠** | 輸入Web伺服器代理埠。 預設為9200<br>Adobe Commerce在雲基礎架構方面：從整合系統中獲取此值。 |
   | **Elasticsearch索引前置詞** | 輸入搜索引擎索引前置詞。 如果將單個實例用於多個Commerce安裝（登台和生產環境），則必須為每個安裝指定一個唯一的前置詞。 否則，可以使用預設前置詞magento2。 |
   | **啟用ElasticsearchHTTP身份驗證** | 按一下 **是** 僅在為搜索引擎伺服器啟用身份驗證時。 如果是，請在提供的欄位中提供用戶名和密碼。 |

1. 按一下 **Test連接**。

   示例響應：

   ![成功](../../assets/configuration/elastic_test-success.png)

   繼續：

   - [為搜索引擎配置Apache](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [為搜索引擎配置nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   或者您看到：

   ![失敗](../../assets/configuration/elastic_test-fail.png)

如果是，請嘗試以下操作：

- 確保搜索引擎伺服器正在運行。
- 如果伺服器位於與Commerce不同的主機上，請登錄到Commerce伺服器並ping搜索引擎主機。 解決網路連接問題並再次test連接。
- 檢查在其中啟動Elasticsearch或OpenSearch的命令窗口，以查找堆棧跟蹤和異常。 必須先解決這些問題，然後才能繼續。 特別是，確保您以用戶身份啟動搜索引擎 `root` 權限。
- 確保 [UNIX防火牆和SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) 都已禁用，或設定規則以使搜索引擎和Commerce能夠相互通信。
- 驗證 **Elasticsearch伺服器主機名** 的子菜單。 確保伺服器可用。 您可以嘗試伺服器的IP地址。
- 使用 `netstat -an | grep <listen-port>` 命令，以驗證在 **Elasticsearch伺服器埠** 其他進程未使用欄位。

   例如，要查看搜索引擎是否在其預設埠上運行，請使用以下命令：

   ```bash
   netstat -an | grep 9200
   ```

   如果它在埠9200上運行，則顯示類似於以下內容：

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 重新索引目錄搜索並刷新全頁快取

更改搜索引擎配置後，必須重新索引目錄搜索索引並使用管理或命令行刷新全頁快取。

使用Admin刷新快取：

1. 在管理員中，按一下 **系統** > **快取管理**。
1. 選中旁邊的複選框 **頁快取**。
1. 從 **操作** 清單，按一下 **刷新**。

   ![快取管理](../../assets/configuration/refresh-cache.png)

使用命令行清除快取： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

要使用命令行重新索引，請執行以下操作：

1. 將Commerce伺服器作為或切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 輸入以下任意命令：

   輸入以下命令以僅重新索引目錄搜索索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   輸入以下命令以重新索引所有索引器：

   ```bash
   bin/magento indexer:reindex
   ```

1. 等待重新索引完成。

   >[!INFO]
   >
   >與快取不同，索引器由cron作業更新。 確保 [啟用cron](../cli/configure-cron-jobs.md) 開始使用搜索引擎。

