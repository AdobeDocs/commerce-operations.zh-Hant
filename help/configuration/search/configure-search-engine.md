---
title: 搜索引擎配置
description: 為Adobe Commerce和Magento Open Source的內部部署配置搜索引擎。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 搜索引擎配置

本節討論在testElasticsearch或OpenSearch時必須選擇的最低設定，包括Adobe Commerce和Magento Open Source的內部部署。

>[!TIP]
>
>在2.4.4和2.4.3-p2版中，所有欄位都標有 **Elasticsearch** 也適用於OpenSearch。
>在2.4.6版中引入對Elasticsearch8.x的支援時，將建立新標籤以區分Elasticsearch和OpenSearch配置。

有關配置搜索引擎的其他詳細資訊，請參閱 [使用手冊](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html)。

## 從管理員配置您的搜索引擎

>[!TIP]
>
>有關升級到新搜索引擎版本的說明，請參見 [升級先決條件](../../upgrade/prepare/prerequisites.md)。

要將系統配置為使用Elasticsearch或OpenSearch，請執行以下操作：

1. 以管理員身份登錄到管理員。
1. 按一下 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**。
1. 從 **[!UICONTROL Search Engine]** 清單中，選擇搜索引擎的相應版本。

   下表列出了配置和test與Commerce的連接所需的選項。 除非您更改了搜索引擎的伺服器設定，否則預設值應有效。 跳至下一步。

   | 選項 | 說明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | 輸入運行Elasticsearch或OpenSearch的電腦的完全限定主機名或IP地址。<br>Adobe Commerce在雲基礎架構方面：從整合系統中獲取此值。 |
   | **[!UICONTROL Server Port]** | 輸入Web伺服器代理埠。 預設為9200<br>Adobe Commerce在雲基礎架構方面：從整合系統中獲取此值。 |
   | **[!UICONTROL Index Prefix]** | 輸入搜索引擎索引前置詞。 如果將單個實例用於多個Commerce安裝（登台和生產環境），則必須為每個安裝指定一個唯一的前置詞。 否則，可以使用預設前置詞magento2。 |
   | **[!UICONTROL Enable HTTP Auth]** | 按一下 **[!UICONTROL Yes]** 僅在為搜索引擎伺服器啟用身份驗證時。 如果是，請在提供的欄位中提供用戶名和密碼。 |
   | **[!UICONTROL Server Timeout]** | 輸入嘗試建立與Elasticsearch或OpenSearch伺服器的連接時等待的時間（秒）。 |

1. 按一下 **[!UICONTROL Test Connection]**。

   示例響應：

   ![成功](../../assets/configuration/elastic_test-success.png)

   繼續：

   - [為搜索引擎配置Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [為搜索引擎配置nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者您看到：

   ![失敗](../../assets/configuration/elastic_test-fail.png)

如果是，請嘗試以下操作：

- 確保搜索引擎伺服器正在運行。
- 如果伺服器位於與Commerce不同的主機上，請登錄到Commerce伺服器並ping搜索引擎主機。 解決網路連接問題並再次test連接。
- 檢查在其中啟動Elasticsearch或OpenSearch的命令窗口，以查找堆棧跟蹤和異常。 必須先解決這些問題，然後才能繼續。 特別是，確保您以用戶身份啟動搜索引擎 `root` 權限。
- 確保 [UNIX防火牆和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 都已禁用，或設定規則以使搜索引擎和Commerce能夠相互通信。
- 驗證 **[!UICONTROL Server Hostname]** 的子菜單。 確保伺服器可用。 您可以嘗試伺服器的IP地址。
- 使用 `netstat -an | grep <listen-port>` 命令，以驗證在 **[!UICONTROL Server Port]** 其他進程未使用欄位。

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

1. 在管理員中，按一下 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**。
1. 選中旁邊的複選框 **[!UICONTROL Page Cache]**。
1. 從 **[!UICONTROL Actions]** 清單，按一下 **刷新**。

   ![快取管理](../../assets/configuration/refresh-cache.png)

使用命令行清除快取： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

要使用命令行重新索引，請執行以下操作：

1. 將Commerce伺服器作為或切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
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
