---
title: 完整必要條件
description: 完成這些先決條件步驟，以準備您的Adobe Commerce專案以進行升級。
source-git-commit: 45c544a5ec9a17ad631fce55e322e2949ecdd3c2
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# 完整升級必要條件

請務必了解執行Adobe Commerce的必要條件。 您必須先檢閱 [系統需求](../../installation/system-requirements.md) 針對您打算升級至的版本。

檢閱系統需求後，您必須先完成下列必要條件，才能升級系統：

* 更新所有軟體
* 確認已安裝支援的搜尋引擎
* 轉換資料庫表格格式
* 設定開啟的檔案限制
* 驗證cron作業是否正在運行
* 設定 `DATA_CONVERTER_BATCH_SIZE`
* 驗證檔案系統權限
* 設定 `pub/` 目錄根目錄
* 安裝撰寫器更新外掛程式

## 更新所有軟體

此 [系統需求](../../installation/system-requirements.md) 說明哪些協力廠商軟體版本已透過Adobe Commerce版本進行測試。

請確定您已更新環境中的所有系統需求和相依性。 參見PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php)，和 [必需的PHP設定](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>針對雲端基礎架構Pro專案上的Adobe Commerce，您必須建立 [支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 在測試和生產環境中安裝或更新服務的票證。 指出所需的服務變更，並包含您的更新 `.magento.app.yaml` 和 `services.yaml` 檔案和PHP版本。 雲端基礎架構團隊最多需要48小時來更新您的專案。 請參閱 [支援的軟體和服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## 確認已安裝支援的搜尋引擎

Adobe Commerce需要安裝Elasticsearch或OpenSearch才能使用軟體。

**如果您從2.3.x升級至2.4**，您必須檢查在2.3.x例項中，您是使用MySQL、Elasticsearch或協力廠商擴充功能作為目錄搜尋引擎。 結果決定了您必須執行的動作 _befor_ 升級至2.4。

**如果要升級2.3.x或2.4.x版本中的修補程式版本**，若已安裝Elasticsearch7.x，您可以選擇 [移轉至OpenSearch](opensearch-migration.md).

您可以使用命令列或管理員來判斷目錄搜尋引擎：

* 輸入 `bin/magento config:show catalog/search/engine` 命令。 命令返回值 `mysql`, `elasticsearch` (表示已設定Elasticsearch2), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`、或自訂值，表示您已安裝協力廠商搜尋引擎。 若為2.4.6之前的版本，請使用 `elasticsearch7` Elasticsearch7或OpenSearch引擎的值。 若為2.4.6版和更新版本，請使用 `opensearch` 的值。

* 從管理員檢查 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 欄位。

以下幾節說明在升級至2.4.0之前，您必須執行哪些動作。

### MySQL

自2.4版起，MySQL不再是支援的目錄搜尋引擎。 升級之前，必須安裝並配置Elasticsearch或OpenSearch。 使用下列資源來協助您完成此程式：

* [安裝和配置Elasticsearch](../../configuration/search/overview-search.md)
* [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 設定 [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) 或 [Apache](../../installation/prerequisites/search-engine/configure-apache.md) 與搜尋引擎搭配使用
* [設定商務以使用Elasticsearch](../../configuration/search/configure-search-engine.md) 重新索引

有些協力廠商目錄搜尋引擎會在Adobe Commerce搜尋引擎上執行。 請連絡您的廠商以判斷您是否必須更新擴充功能。

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 搜尋引擎

在升級至2.4.0之前，必須安裝並配置Elasticsearch7.6或更高版本，或OpenSearch 1.2。Adobe不再支援Elasticsearch2.x、5.x和6.x。 [搜尋引擎設定](../../configuration/search/configure-search-engine.md) 在 _配置指南_ 說明將Elasticsearch升級至支援的版本後，您必須執行的工作。

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關在部署到生產環境之前備份資料、檢測潛在遷移問題和測試升級的完整說明。 視您當前的Elasticsearch版本而定，可能需要或不需要完全群集重新啟動。

Elasticsearch需要Java開發套件(JDK)1.8或更新版本。 請參閱 [安裝Java軟體開發套件(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 來檢查安裝的JDK版本。

#### OpenSearch

OpenSearch是Elasticsearch7.10.2的開放原始碼復本，在Elasticsearch授權變更後進行。 下列Adobe Commerce版本推出OpenSearch支援：

* 2.4.6（OpenSearch有單獨的模組和設定）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

您可以 [從Elasticsearch移轉至OpenSearch](opensearch-migration.md) 只有在您升級至以上所列的Adobe Commerce版本（或更新版本）時。

OpenSearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發套件(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 來檢查安裝的JDK版本。

[搜尋引擎設定](../../configuration/search/configure-search-engine.md) 說明變更搜尋引擎後必須執行的工作。

#### 升級Elasticsearch

Adobe Commerce 2.4.6已推出對Elasticsearch8.x的支援。下列指示顯示將Elasticsearch從7.x升級至8.x的範例：

1. 將Elasticsearch7.x伺服器升級至8.x，並確定已啟動並正在執行。 請參閱 [Elasticsearch檔案](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. 啟用 `id_field_data` 欄位，將下列設定新增至 `elasticsearch.yml` 檔案並重新啟動Elasticsearch8.x服務。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >為支援Elasticsearch8.x,Adobe Commerce 2.4.6不允許 `indices.id_field_data` 屬性，並使用 `_id` 欄位 `docvalue_fields` 屬性。

1. 在Adobe Commerce專案的根目錄中，更新您的撰寫器相依性以移除 `Magento_Elasticsearch7` 模組和安裝 `Magento_Elasticsearch8` 模組。

   ```bash
   composer update magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. 更新專案元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 在 [!DNL Admin].

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取類型中刪除所有項。

   ```bash
   bin/magento cache:clean
   ```

#### 降級Elasticsearch

如果您不小心升級了伺服器上的Elasticsearch版本，或因任何其他原因而確定需要降級，則還必須更新Adobe Commerce項目依賴項。 例如，要從Elasticsearch8.x降級到7.x

1. 將Elasticsearch8.x伺服器降級為7.x，並確保已啟動並正在運行。 請參閱 [Elasticsearch檔案](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. 在Adobe Commerce專案的根目錄中，更新您的撰寫器相依性以移除 `Magento_Elasticsearch8` 模組及其撰寫器相依性並安裝 `Magento_Elasticsearch7` 模組。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. 更新專案元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 在 [!DNL Admin].

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取類型中刪除所有項。

   ```bash
   bin/magento cache:clean
   ```

### 協力廠商擴充功能

建議您聯絡搜尋引擎廠商，判斷您的擴充功能是否與Adobe Commerce版本完全相容。

## 轉換資料庫表格格式

必須從 `COMPACT` to `DYNAMIC`. 您還必須從 `MyISAM` to `InnoDB`. 請參閱 [最佳實務](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## 設定開啟的檔案限制

設定開啟的檔案限制(ulimit)有助於避免因多次遞歸調用長查詢字串而失敗，或使用 `bin/magento setup:rollback` 命令。 對於不同的UNIX殼，此命令不同。 如需詳細資訊，請參閱您的個別口味 `ulimit` 命令。

Adobe建議設定開啟的檔案 [上限](https://ss64.com/bash/ulimit.html) 的值 `65536` 或更多，但您可以視需要使用較大的值。 您可以在命令列上設定上限，或將其設為使用者殼層的永久設定。

要從命令行設定上限，請執行以下操作：

1. 切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 將上限設為 `65536`.

   ```bash
   ulimit -n 65536
   ```

要在Bash殼層中設定值：

1. 切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 開啟 `/home/<username>/.bashrc` 在文字編輯器中。
1. 新增下列行：

   ```bash
   ulimit -n 65536
   ```

1. 將變更儲存至 `.bashrc` 檔案，然後退出文字編輯器。

>[!IMPORTANT]
>
>建議您避免為 `pcre.recursion_limit` 屬性 `php.ini` 檔案，因為它可能導致回傳不完整，且沒有失敗通知。

## 驗證cron作業是否正在運行

UNIX任務調度程式 `cron` 對於日常Adobe Commerce作業至關重要。 它會排程重新索引、電子報、電子郵件和網站地圖等項目。 若干功能至少需要以檔案系統擁有者身分執行一個cron工作。

要驗證cron作業是否已正確設定，請輸入以下命令作為檔案系統所有者以檢查crontab :

>[!NOTE]
>
>crontab是負責執行cron作業的設定檔案。

```bash
crontab -l
```

應顯示類似下列的結果：

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

未執行cron的另一個症狀是管理員中的下列錯誤：

![](../../assets/upgrade-guide/cron-not-running.png)

若要查看錯誤，請按一下 **系統消息** ，如下所示：

![](../../assets/upgrade-guide/system-messages.png)

請參閱 [設定並執行cron](../../configuration/cli/configure-cron-jobs.md) 以取得更多資訊。

## 設定DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4包含安全性增強功能，需要將部分資料從序列化轉換為JSON。 此轉換會在升級期間進行，而且可能需要很長時間，具體取決於您的資料庫中有多少資料。

下表對影響最大：

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

如果您有大量資料，則可設定環境變數的值，以改善效能。 `DATA_CONVERTER_BATCH_SIZE`. 預設情況下，值會設為 `50,000`.

若要設定環境變數：

1. 切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 設定變數：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 需要記憶體；請避免先將其設為大值（約1 GB），不要先進行測試。

1. 升級完成後，您可以取消設定變數：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 驗證檔案系統權限

基於安全考量，Adobe Commerce需要檔案系統的特定權限。 權限與 _[所有權](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. 所有權決定了誰可以在檔案系統上執行操作；權限決定了使用者的功能。

檔案系統中的目錄必須由 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md) 群組。

要驗證檔案系統權限設定是否正確，請登錄到應用程式伺服器，或使用托管提供商的檔案管理器應用程式。

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

如需範例輸出的說明，請參閱下列內容：

* 大部分檔案 `-rw-rw----`，即 `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* 檔案系統所有者是 `magento_user`

要獲取更詳細的資訊，可以輸入以下命令：

```bash
ls -la /var/www/html/magento2/pub
```

因為Adobe Commerce會將靜態檔案資產部署至的子目錄 `pub`，也建議您驗證其權限和所有權。

如需詳細資訊，請參閱 [檔案系統權限和所有權](../../installation/prerequisites/file-system/overview.md).

## 設定 `pub/` 目錄根目錄

請參閱 [修改docroot以提高安全性](../../installation/tutorials/docroot.md) 以取得更多詳細資訊。

## 安裝撰寫器更新外掛程式

此 [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) 撰寫器外掛程式解析必須對根專案進行的變更 `composer.json` 檔案，然後再更新為新產品需求。

外掛程式可借由識別並協助您解決相依性衝突，而非要求您手動識別和修正相依性衝突，部分自動化手動升級。

若要安裝外掛程式：

1. 將套件新增至 `composer.json` 檔案。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 更新相依性：

   ```bash
   composer update
   ```
