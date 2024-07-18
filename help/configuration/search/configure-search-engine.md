---
title: 搜尋引擎設定
description: 設定Adobe Commerce內部部署的搜尋引擎。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 搜尋引擎設定

本節討論測試Elasticsearch或OpenSearch與Adobe Commerce內部部署所需的最低設定。

>[!TIP]
>
>在2.4.4和2.4.3-p2版中，所有標示為&#x200B;**Elasticsearch**的欄位也適用於OpenSearch。
>2.4.6版開始支援Elasticsearch8.x時，建立了新標籤以區分Elasticsearch和OpenSearch設定。

如需設定搜尋引擎的詳細資訊，請參閱[使用手冊](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html)。

## 從管理員設定搜尋引擎

>[!TIP]
>
>如需升級至新搜尋引擎版本的指示，請參閱[升級必要條件](../../upgrade/prepare/prerequisites.md)。

若要設定您的系統以使用Elasticsearch或OpenSearch：

1. 以管理員身分登入管理員。
1. 按一下&#x200B;**[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**。
1. 從&#x200B;**[!UICONTROL Search Engine]**&#x200B;清單中，選取搜尋引擎的對應版本。

   下表列出設定和測試與Commerce的連線所需的選項。 除非您變更搜尋引擎的伺服器設定，否則預設值應該有效。 跳至下一個步驟。

   | 選項 | 說明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | 輸入執行Elasticsearch或OpenSearch之電腦的完整主機名稱或IP位址。雲端基礎結構上的<br>Adobe Commerce：從您的整合系統取得此值。 |
   | **[!UICONTROL Server Port]** | 輸入Web伺服器Proxy連線埠。 雲端基礎結構上的預設值為9200<br>Adobe Commerce：從您的整合系統中取得此值。 |
   | **[!UICONTROL Index Prefix]** | 輸入搜尋引擎索引前置詞。 如果您將單一執行個體用於多個Commerce安裝（測試和生產環境），則必須為每次安裝指定唯一的前置詞。 否則，您可以使用預設首碼magento2。 |
   | **[!UICONTROL Enable HTTP Auth]** | 只有在您已啟用搜尋引擎伺服器的驗證時，才按一下&#x200B;**[!UICONTROL Yes]**。 若是如此，請在提供的欄位中提供使用者名稱和密碼。 |
   | **[!UICONTROL Server Timeout]** | 輸入嘗試建立與Elasticsearch或OpenSearch伺服器的連線時等待的時間長度（以秒為單位）。 |

1. 按一下&#x200B;**[!UICONTROL Test Connection]**。

   範例回應：

   ![成功](../../assets/configuration/elastic_test-success.png)

   繼續使用：

   - [為您的搜尋引擎設定Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [為您的搜尋引擎設定nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者，您會看到：

   ![失敗](../../assets/configuration/elastic_test-fail.png)

若是如此，請嘗試下列步驟：

- 請確定搜尋引擎伺服器執行中。
- 如果伺服器與Commerce位於不同的主機上，請登入Commerce伺服器並Ping搜尋引擎主機。 解決網路連線問題，並再次測試連線。
- 檢查您開始Elasticsearch的命令視窗或OpenSearch，以找出棧疊追蹤和例外狀況。 您必須先解決這些問題，才能繼續。 特別是，請確定您是以具有`root`許可權的使用者身份啟動您的搜尋引擎。
- 請確定[UNIX防火牆和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux)皆已停用，或設定規則讓您的搜尋引擎和Commerce能夠相互通訊。
- 驗證&#x200B;**[!UICONTROL Server Hostname]**&#x200B;欄位的值。 確定伺服器可供使用。 您可以改為嘗試伺服器的IP位址。
- 使用`netstat -an | grep <listen-port>`命令確認&#x200B;**[!UICONTROL Server Port]**&#x200B;欄位中指定的連線埠並未由其他處理序使用。

  例如，若要檢視搜尋引擎是否在其預設連線埠上執行，請使用下列命令：

  ```bash
  netstat -an | grep 9200
  ```

  如果是在連線埠9200上執行，則會顯示類似下列的內容：

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## 重新索引目錄搜尋並重新整理整頁快取

變更搜尋引擎組態之後，您必須重新索引目錄搜尋索引，並使用管理員或命令列重新整理整頁快取。

若要使用Admin重新整理快取：

1. 在Admin中，按一下&#x200B;**[!UICONTROL System]** > **[!UICONTROL Cache Management]**。
1. 選取&#x200B;**[!UICONTROL Page Cache]**&#x200B;旁的核取方塊。
1. 從右上角的&#x200B;**[!UICONTROL Actions]**&#x200B;清單中，按一下&#x200B;**重新整理**。

   ![快取管理](../../assets/configuration/refresh-cache.png)

若要使用命令列清除快取： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

使用命令列重新索引：

1. 以或切換到[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的Commerce伺服器。
1. 輸入下列任一命令：

   輸入以下命令，只將目錄搜尋索引重新編列索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   輸入下列命令以重新索引所有索引子：

   ```bash
   bin/magento indexer:reindex
   ```

1. 等候重新索引完成。

   >[!INFO]
   >
   >和快取不同，索引子會由cron作業更新。 在您開始使用搜尋引擎之前，請確定[cron已啟用](../cli/configure-cron-jobs.md)。
