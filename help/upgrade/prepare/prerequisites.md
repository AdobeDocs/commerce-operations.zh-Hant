---
title: 完成先決條件
description: 通過完成這些先決條件步驟，準備您的Adobe Commerce項目進行升級。
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# 完成升級先決條件

瞭解管理Adobe Commerce的必要性很重要。 您必須首先查看 [系統要求](../../installation/system-requirements.md) 版本。

在複查系統要求後，必須先完成以下先決條件，然後才能升級系統：

* 更新所有軟體
* 驗證是否安裝了支援的搜索引擎
* 轉換資料庫表格式
* 設定開啟的檔案限制
* 驗證cron作業是否正在運行
* 設定 `DATA_CONVERTER_BATCH_SIZE`
* 驗證檔案系統權限
* 設定 `pub/` 目錄根目錄
* 安裝Composer更新插件

## 更新所有軟體

的 [系統要求](../../installation/system-requirements.md) 具體描述哪些第三方軟體版本已在Adobe Commerce版本中測試。

確保更新環境中的所有系統要求和依賴項。 參見PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), [所需的PHP設定](../../installation/prerequisites/php-settings.md#php-settings)。

>[!NOTE]
>
>對於Adobe Commerce的雲基礎架構Pro項目，您必須建立 [支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 在暫存和生產環境中安裝或更新服務的票證。 指示所需的服務更改並包括更新的 `.magento.app.yaml` 和 `services.yaml` 票證中的檔案和PHP版本。 雲基礎架構團隊最多需要48小時才能更新您的項目。 請參閱 [支援的軟體和服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services)。

## 驗證是否安裝了支援的搜索引擎

Adobe Commerce需要安裝Elasticsearch或OpenSearch才能使用軟體。

**如果要從2.3.x升級到2.4**，您必須檢查在2.3.x實例中是使用MySQL、Elasticsearch還是第三方擴展作為目錄搜索引擎。 結果決定了您必須做什麼 _先_ 升級到2.4。

**如果要升級2.3.x或2.4.x發行版中的補丁程式版本**，如果已安裝Elasticsearch7.x，則您可以選擇 [遷移到OpenSearch](opensearch-migration.md)。

您可以使用命令行或管理員來確定目錄搜索引擎：

* 輸入 `bin/magento config:show catalog/search/engine` 的子菜單。 該命令返回的值 `mysql`。 `elasticsearch` (表示已配置Elasticsearch2), `elasticsearch5`。 `elasticsearch6`。 `elasticsearch7`或自定義值，表示您已安裝第三方搜索引擎。 對於2.4.6之前的版本，請使用 `elasticsearch7` Elasticsearch7或OpenSearch引擎的值。 對於2.4.6版和更高版本，請使用 `opensearch` OpenSearch引擎的值。

* 在管理員中，檢查 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 的子菜單。

以下各節介紹升級到2.4.0之前必須執行的操作。

### MySQL

從2.4開始，MySQL不再是受支援的目錄搜索引擎。 升級前必須安裝和配置Elasticsearch或OpenSearch。 使用以下資源幫助您完成此過程：

* [安裝和配置Elasticsearch](../../configuration/search/overview-search.md)
* [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 配置 [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) 或 [阿帕奇](../../installation/prerequisites/search-engine/configure-apache.md) 使用搜索引擎
* [將Commerce配置為使用Elasticsearch](../../configuration/search/configure-search-engine.md) 重新索引

一些第三方目錄搜索引擎在Adobe Commerce搜索引擎上運行。 聯繫您的供應商以確定您是否必須更新擴展。

#### 瑪麗亞

{{$include /help/_includes/maria-db-config.md}}

### 搜索引擎

在升級到2.4.0之前，必須安裝並配置Elasticsearch7.6或更高版本或OpenSearch 1.2。Adobe不再支援Elasticsearch2.x、5.x和6.x。 [搜索引擎配置](../../configuration/search/configure-search-engine.md) 的 _配置指南_ 描述將Elasticsearch升級到受支援版本後必須執行的任務。

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關備份資料、檢測潛在遷移問題和在部署到生產之前測試升級的完整說明。 根據您當前版本的Elasticsearch，可能需要或不需要完全群集重新啟動。

Elasticsearch需要Java開發工具包(JDK)1.8或更高版本。 請參閱 [安裝Java軟體開發工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 以檢查安裝的JDK版本。

#### 開啟搜索

OpenSearch是Elasticsearch7.10.2的開源分叉，在Elasticsearch更改許可後。 以下版本的Adobe Commerce引入了對OpenSearch的支援：

* 2.4.6（OpenSearch有單獨的模組和設定）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

你可以 [從Elasticsearch遷移到OpenSearch](opensearch-migration.md) 只有升級到上面列出的Adobe Commerce版本（或更高版本）。

OpenSearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 以檢查安裝的JDK版本。

[搜索引擎配置](../../configuration/search/configure-search-engine.md) 描述了更改搜索引擎後必須執行的任務。

#### 升級Elasticsearch

Adobe Commerce對8.x號Elasticsearch的支援在2.4.6。以下說明顯示了將Elasticsearch從7.x升級到8.x的示例：

1. 將Elasticsearch7.x伺服器升級到8.x，並確保已啟動並正在運行。 查看 [Elasticsearch文檔](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 啟用 `id_field_data` 將以下配置添加到 `elasticsearch.yml` 檔案並重新啟動Elasticsearch8.x服務。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >為支援Elasticsearch8.x,Adobe Commerce2.4.6不允許 `indices.id_field_data` 預設情況下使用屬性 `_id` 的 `docvalue_fields` 屬性。

1. 在您的Adobe Commerce項目的根目錄中，更新您的Composer依賴項以刪除 `Magento_Elasticsearch7` 並安裝 `Magento_Elasticsearch8` 中。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. 更新項目元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 的 [!DNL Admin]。

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取類型中刪除所有項。

   ```bash
   bin/magento cache:clean
   ```

#### 降級Elasticsearch

如果您無意中升級了伺服器上的Elasticsearch版本，或由於任何其他原因確定需要降級，則還必須更新您的Adobe Commerce項目依賴項。 例如，要從Elasticsearch8.x降級到7.x

1. 將Elasticsearch8.x伺服器降級為7.x，並確保已啟動並正在運行。 查看 [Elasticsearch文檔](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 在您的Adobe Commerce項目的根目錄中，更新您的Composer依賴項以刪除 `Magento_Elasticsearch8` 模組及其Composer依賴項，並安裝 `Magento_Elasticsearch7` 中。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. 更新項目元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 的 [!DNL Admin]。

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取類型中刪除所有項。

   ```bash
   bin/magento cache:clean
   ```

### 第三方擴展

我們建議您與搜索引擎供應商聯繫，以確定您的擴展是否與Adobe Commerce版完全相容。

## 轉換資料庫表格式

必須轉換所有資料庫表的格式 `COMPACT` 至 `DYNAMIC`。 您還必須從 `MyISAM` 至 `InnoDB`。 請參閱 [最佳做法](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)。

## 設定開啟的檔案限制

設定開啟的檔案限制(ulimit)有助於避免因多次遞歸調用長查詢字串或使用 `bin/magento setup:rollback` 的子菜單。 此命令對於不同的UNIX外殼不同。 請參考您的個性化特點，瞭解 `ulimit` 的子菜單。

Adobe建議設定開啟的檔案 [上限](https://ss64.com/bash/ulimit.html) 值 `65536` 或更多，但必要時可以使用更大的值。 可以在命令行上設定ulimit ，也可以將其設定為用戶shell的永久設定。

要從命令行設定限制：

1. 切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 將限制設定為 `65536`。

   ```bash
   ulimit -n 65536
   ```

要在Bash外殼中設定值：

1. 切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 開啟 `/home/<username>/.bashrc` 的子菜單。
1. 添加以下行：

   ```bash
   ulimit -n 65536
   ```

1. 保存對 `.bashrc` 並退出文本編輯器。

>[!IMPORTANT]
>
>建議您避免為 `pcre.recursion_limit` 屬性 `php.ini` 檔案，因為它可能導致不完整的回滾，且沒有失敗通知。

## 驗證cron作業是否正在運行

UNIX任務計畫程式 `cron` 是Adobe Commerce日常運作的關鍵。 它會安排諸如重新編製索引、新聞通訊、電子郵件和小小集之類的活動。 若干功能要求至少以檔案系統所有者身份運行一個cron作業。

要驗證是否正確設定了cron作業，請輸入以下命令作為檔案系統所有者來檢查crontab:

>[!NOTE]
>
>crontab是負責運行cron作業的配置檔案。

```bash
crontab -l
```

應顯示類似於以下結果：

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

cron未運行的另一個症狀是管理中出現以下錯誤：

![](../../assets/upgrade-guide/cron-not-running.png)

要查看錯誤，請按一下 **系統消息** 窗口頂部，如下所示：

![](../../assets/upgrade-guide/system-messages.png)

請參閱 [配置並運行cron](../../configuration/cli/configure-cron-jobs.md) 的子菜單。

## 設定DATA_CONVERTER_BATCH_SIZE

Adobe Commerce2.4包含安全增強功能，要求將某些資料從序列化轉換為JSON。 此轉換在升級過程中發生，可能需要很長時間，具體取決於資料庫中有多少資料。

下表受影響最大：

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

如果您有大量資料，則可以通過設定環境變數的值來提高效能， `DATA_CONVERTER_BATCH_SIZE`。 預設情況下，值設定為 `50,000`。

要設定環境變數：

1. 切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 設定變數：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 需要記憶體；避免將其設定為大值（大約1 GB），而不先測試它。

1. 升級完成後，可以取消設定變數：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 驗證檔案系統權限

出於安全原因，Adobe Commerce需要對檔案系統具有某些權限。 權限與 _[所有權](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_。 所有權決定誰可以對檔案系統執行操作；權限決定用戶可以做什麼。

檔案系統中的目錄必須由 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md) 組。

要驗證檔案系統權限是否設定正確，請登錄到應用程式伺服器或使用托管提供程式的檔案管理器應用程式。

例如，如果應用程式安裝在 `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

示例輸出：

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

有關示例輸出的說明，請參見以下內容：

* 大多數檔案 `-rw-rw----`，即 `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* 檔案系統所有者是 `magento_user`

要獲取更多詳細資訊，可以輸入以下命令：

```bash
ls -la /var/www/html/magento2/pub
```

因為Adobe Commerce將靜態檔案資產部署到 `pub`，驗證權限和所有權也是一個好主意。

有關詳細資訊，請參見 [檔案系統權限和所有權](../../installation/prerequisites/file-system/overview.md)。

## 設定 `pub/` 目錄根目錄

請參閱 [修改docroot以提高安全性](../../installation/tutorials/docroot.md) 的子菜單。

## 安裝Composer更新插件

的 [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) 作曲家插件解析必須對根項目所做的更改 `composer.json` 檔案，然後更新到新產品要求。

該插件通過識別並幫助您解決依賴關係衝突而不是要求您手動識別和修復它們，部分地自動化了手動升級。

安裝插件：

1. 將包添加到 `composer.json` 的子菜單。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 更新依賴項：

   ```bash
   composer update
   ```
