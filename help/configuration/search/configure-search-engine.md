---
title: 搜尋引擎設定
description: 為Adobe Commerce和Magento Open Source的內部部署設定搜尋引擎。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# 搜尋引擎設定

本節探討在Adobe Commerce和Magento Open Source的內部部署中，測試Elasticsearch或OpenSearch時必須選擇的最低設定。

>[!TIP]
>
>在2.4.4和2.4.3-p2版中，所有欄位都標示為 **Elasticsearch** 也適用於OpenSearch。
>2.4.6版推出對Elasticsearch8.x的支援時，已建立新標籤以區分Elasticsearch和OpenSearch設定。

如需設定搜尋引擎的其他詳細資訊，請參閱 [使用手冊](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 從管理員設定您的搜尋引擎

>[!TIP]
>
>如需升級至新搜尋引擎版本的相關指示，請參閱 [升級必要條件](../../upgrade/prepare/prerequisites.md).

要配置系統以使用Elasticsearch或OpenSearch，請執行以下操作：

1. 以管理員身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 從 **[!UICONTROL Search Engine]** 清單中，選取搜尋引擎的對應版本。

   下表列出使用Commerce設定和測試連線所需的選項。 除非您變更了搜尋引擎的伺服器設定，否則預設值應可運作。 跳到下一步。

   | 選項 | 說明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | 輸入運行Elasticsearch或OpenSearch的電腦的完全限定主機名或IP地址。<br>Adobe Commerce雲基礎架構：從整合系統取得此值。 |
   | **[!UICONTROL Server Port]** | 輸入Web伺服器代理埠。 預設為9200<br>Adobe Commerce雲基礎架構：從整合系統取得此值。 |
   | **[!UICONTROL Index Prefix]** | 輸入搜尋引擎索引首碼。 如果您對多個商務安裝（測試和生產環境）使用單一例項，則必須為每個安裝指定唯一的前置詞。 否則，您可以使用預設首碼magento2。 |
   | **[!UICONTROL Enable HTTP Auth]** | 按一下 **[!UICONTROL Yes]** 只有在您為搜尋引擎伺服器啟用驗證時。 若有，請在提供的欄位中提供使用者名稱和密碼。 |
   | **[!UICONTROL Server Timeout]** | 輸入嘗試建立與Elasticsearch或OpenSearch伺服器的連接時要等待的時間（以秒為單位）。 |

1. 按一下 **[!UICONTROL Test Connection]**.

   範例回應：

   ![成功](../../assets/configuration/elastic_test-success.png)

   繼續：

   - [為您的搜尋引擎設定Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [為搜尋引擎設定nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者你看到：

   ![失敗](../../assets/configuration/elastic_test-fail.png)

如果是，請嘗試下列步驟：

- 請確定搜尋引擎伺服器執行中。
- 如果伺服器與Commerce位於不同的主機，請登入Commerce伺服器並偵測搜尋引擎主機。 解決網路連接問題並再次測試連接。
- 檢查在其中啟動Elasticsearch的命令窗口，或OpenSearch查找堆棧跟蹤和異常。 在繼續之前，您必須先解決這些問題。 尤其是，請務必以使用者身分啟動搜尋引擎 `root` 權限。
- 確保 [UNIX防火牆和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 都已停用，或設定規則，讓您的搜尋引擎和商務可互相通訊。
- 驗證 **[!UICONTROL Server Hostname]** 欄位。 確保伺服器可用。 您可以改用伺服器的IP位址。
- 使用 `netstat -an | grep <listen-port>` 命令，驗證 **[!UICONTROL Server Port]** 欄位未供其他程式使用。

   例如，若要查看您的搜尋引擎是否在其預設埠上執行，請使用下列命令：

   ```bash
   netstat -an | grep 9200
   ```

   如果它在埠9200上運行，則顯示如下：

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 重新索引目錄搜尋並重新整理整頁快取

變更搜尋引擎設定後，您必須重新索引目錄搜尋索引，並使用管理員或命令列重新整理整頁快取。

若要使用管理員重新整理快取：

1. 在管理員中，按一下 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 選取旁邊的核取方塊 **[!UICONTROL Page Cache]**.
1. 從 **[!UICONTROL Actions]** 清單，按一下 **重新整理**.

   ![快取管理](../../assets/configuration/refresh-cache.png)

使用命令行清除快取： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

要使用命令行重新索引：

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 輸入以下任一命令：

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
   >與快取不同，索引器是由cron作業更新。 請確定 [cron已啟用](../cli/configure-cron-jobs.md) 開始使用搜尋引擎之前。

