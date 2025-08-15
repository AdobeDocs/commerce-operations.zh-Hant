---
title: 完成必要條件
description: 完成這些先決條件步驟，準備您的Adobe Commerce專案以進行升級。
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: df185e21f918d32ed5033f5db89815b5fc98074f
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# 完成升級必要條件

請務必瞭解執行Adobe Commerce的必要條件。 您必須先檢閱您計畫升級至之版本的[系統需求](../../installation/system-requirements.md)。

檢閱系統需求後，您必須先完成下列必要條件，才能升級系統：

* 更新所有軟體
* 確認已安裝支援的搜尋引擎
* 轉換資料庫表格格式
* 設定開啟檔案限制
* 確認cron工作正在執行
* 設定`DATA_CONVERTER_BATCH_SIZE`
* 驗證檔案系統許可權
* 設定`pub/`目錄根目錄
* 安裝撰寫器更新外掛程式

## 更新所有軟體

[系統需求](../../installation/system-requirements.md)確切說明哪些協力廠商軟體版本已通過Adobe Commerce發行版本測試。

請確定您更新了環境中的所有系統需求和相依性。 請參閱PHP [7.4](https://www.php.net/manual/en/migration74.php)、PHP [8.0](https://www.php.net/manual/en/migration80.php)、PHP [8.1](https://www.php.net/manual/en/migration81.php)和[必要的PHP設定](../../installation/prerequisites/php-settings.md#php-settings)。

>[!NOTE]
>
>對於雲端基礎結構專業專案上的Adobe Commerce，您必須建立[支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant#submit-ticket)票證，才能在中繼和生產環境中安裝或更新服務。 指示所需的服務變更，並將更新的`.magento.app.yaml`和`services.yaml`檔案及PHP版本加入票證中。 雲端基礎結構團隊更新您的專案最多可能需要48小時的時間。 請參閱[支援的軟體與服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html?lang=zh-Hant#supported-software-and-services)。

## 確認已安裝支援的搜尋引擎

Adobe Commerce需要安裝Elasticsearch或OpenSearch才能使用軟體。

**如果您要從2.3.x升級至2.4**，您必須檢查您是否使用MySQL、Elasticsearch或協力廠商擴充功能作為2.3.x執行個體的目錄搜尋引擎。 結果會決定您必須在&#x200B;_升級至2.4之前_&#x200B;做什麼。

**如果您要在2.3.x或2.4.x版本行內升級修補程式版本**，如果已安裝Elasticsearch 7.x，您可以選擇性[移轉至OpenSearch](opensearch-migration.md)。

您可以使用命令列或管理員來決定您的目錄搜尋引擎：

* 輸入`bin/magento config:show catalog/search/engine`命令。 命令傳回值`mysql`、`elasticsearch` (表示已設定Elasticsearch 2)、`elasticsearch5`、`elasticsearch6`、`elasticsearch7`或自訂值，表示您已安裝協力廠商搜尋引擎。 若是2.4.6之前的版本，請使用Elasticsearch 7或OpenSearch引擎的`elasticsearch7`值。 若是2.4.6版或更新版本，請使用OpenSearch引擎的`opensearch`值。

* 從Admin檢查&#x200B;**[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]**&#x200B;欄位的值。

以下小節說明在升級至2.4.0之前必須採取的動作。

### MySQL

自2.4版起，MySQL不再支援目錄搜尋引擎。 升級前，您必須先安裝並設定Elasticsearch或OpenSearch。 請使用下列資源來協助引導您完成此程式：

* [安裝及設定Elasticsearch](../../configuration/search/overview-search.md)
* [正在安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 設定[nginx](../../installation/prerequisites/search-engine/configure-nginx.md)或[Apache](../../installation/prerequisites/search-engine/configure-apache.md)以搭配您的搜尋引擎使用
* [設定Commerce以使用Elasticsearch](../../configuration/search/configure-search-engine.md)並重新索引

部分協力廠商目錄搜尋引擎會在Adobe Commerce搜尋引擎上方執行。 請聯絡您的供應商，以決定是否必須更新擴充功能。

### MySQL 8.4變更

Adobe已在2.4.8版本中新增對MySQL 8.4的支援。
本節說明開發人員應注意的MySQL 8.4重大變更。

#### 過時的非標準金鑰

使用非唯一或部份索引鍵做為外部索引鍵是不標準的，在MySQL 8.4中已過時。從MySQL 8.4.0開始，您必須透過將[`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key)設定為`OFF`或以`--skip-restrict-fk-on-non-standard-key`選項啟動伺服器來明確啟用這類金鑰。

#### 從MySQL 8.0 （或更舊版本）升級至MySQL 8.4

若要將MySQL從8.0版正確升級至8.4版，您必須依照下列順序執行步驟：

1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 進行資料庫備份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 將MySQL升級至8.4版。
1. 在`restrict_fk_on_non_standard_key`檔案的`OFF`中將`[mysqld]`設定為`my.cnf`。

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >如果您未將`restrict_fk_on_non_standard_key`的值變更為`OFF`，則在匯入期間將會出現下列錯誤：
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. 重新啟動MySQL伺服器。
1. 將備份的資料匯入MySQL。
1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 停用維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 搜尋引擎

在升級至2.4.0之前，您必須安裝並設定Elasticsearch 7.6或更新版本或OpenSearch 1.2。Adobe不再支援Elasticsearch 2.x、5.x和6.x。[搜尋引擎組態](../../configuration/search/configure-search-engine.md)組態指南&#x200B;_中的_&#x200B;說明將Elasticsearch升級至支援的版本後，您必須執行的工作。

請參閱[升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)，以取得有關備份資料、偵測可能的移轉問題，以及在部署到生產環境之前測試升級的完整指示。 根據您目前的Elasticsearch版本，不一定需要重新啟動完整叢集。

Elasticsearch需要Java Development Kit (JDK) 1.8或更新版本。 請參閱[安裝Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)以檢查已安裝的JDK版本。

#### OpenSearch

OpenSearch是Elasticsearch授權變更後，Elasticsearch 7.10.2的開放原始碼復本。 下列版本的Adobe Commerce皆支援OpenSearch：

* 2.4.6 （OpenSearch有單獨的模組和設定）
* 2.4.5
* 2.4.4
* 2.4.3 - p2
* 2.3.7 - p3

您必須升級至上述（或更新版本）的Elasticsearch版本，才能[從Adobe Commerce移轉至OpenSearch](opensearch-migration.md)。

OpenSearch需要JDK 1.8或更新版本。 請參閱[安裝Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)以檢查已安裝的JDK版本。

[搜尋引擎組態](../../configuration/search/configure-search-engine.md)說明您在變更搜尋引擎後必須執行的工作。

#### 升級Elasticsearch

Adobe Commerce 2.4.6已匯入對Elasticsearch 8.x的支援。下列指示顯示Elasticsearch從7.x升級至8.x的範例：

>[!NOTE]
>
>在即將發行的2.4.8版本中，這些步驟將不是必要的，因為預設會包含Elasticsearch 8模組，且您不需要另外安裝。

1. 將Elasticsearch 7.x伺服器升級至8.x，並確定已啟動且執行中。 請參閱[Elasticsearch檔案](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 將下列設定新增至您的`id_field_data`檔案並重新啟動Elasticsearch 8.x服務，以啟用`elasticsearch.yml`欄位。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >為了支援Elasticsearch 8.x，Adobe Commerce 2.4.6預設不允許使用`indices.id_field_data`屬性，並使用`_id`屬性中的`docvalue_fields`欄位。

1. 在Adobe Commerce專案的根目錄中，更新您的撰寫器相依性以移除`Magento_Elasticsearch7`模組並安裝`Magento_Elasticsearch8`模組。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   如果您遇到`psr/http-message`的相依性錯誤，請按一下以展開下列疑難排解區段：

   +++疑難排解

   如果在安裝Elasticsearch 8時遇到相依性衝突，尤其是與`psr/http-message`的衝突，您可以按照以下步驟解決此問題：

   1. 首先，需要Elasticsearch 8模組，而不更新其他相依性：

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. 然後更新Elasticsearch 8模組和`aws/aws-sdk-php`套件：

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   此方法適用於2.4.7-p4與PHP 8.3。發生此問題的原因是`aws/aws-sdk-php`需要`psr/http-message >= 2.0`，這可能會造成衝突。 上述步驟有助於解決這些相依性問題。

   +++

1. 更新您的專案元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. 在[中](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin)設定Elasticsearch[!DNL Admin]。

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取型別中刪除所有專案。

   ```bash
   bin/magento cache:clean
   ```

#### 降級Elasticsearch

如果您不小心升級伺服器上的Elasticsearch版本，或因任何其他原因而決定需要降級，您也必須更新Adobe Commerce專案相依性。 例如，若要從Elasticsearch 8.x降級為7.x

1. 將Elasticsearch 8.x伺服器降級為7.x，並確定已啟動且執行中。 請參閱[Elasticsearch檔案](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 在Adobe Commerce專案的根目錄中，更新您的撰寫器相依性以移除`Magento_Elasticsearch8`模組及其撰寫器相依性，並安裝`Magento_Elasticsearch7`模組。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. 更新您的專案元件。

   ```bash
   bin/magento setup:upgrade
   ```

1. 在[中](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin)設定Elasticsearch[!DNL Admin]。

1. 重新索引目錄索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 從啟用的快取型別中刪除所有專案。

   ```bash
   bin/magento cache:clean
   ```

### 協力廠商擴充功能

建議您連絡搜尋引擎廠商，判斷擴充功能是否與Adobe Commerce版本完全相容。

## 轉換資料庫表格格式

您必須將所有資料庫表格的格式從`COMPACT`轉換為`DYNAMIC`。 您也必須將儲存引擎型別從`MyISAM`轉換為`InnoDB`。 請參閱[最佳實務](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)。

## 設定開啟檔案限制

設定開啟檔案限制(ulimit)可協助避免多次遞回呼叫長查詢字串失敗，或避免使用`bin/magento setup:rollback`命令時發生問題。 這個指令對於不同的UNIX殼層是不同的。 如需有關`ulimit`命令的具體資訊，請諮詢您的個人風格。

Adobe建議將開啟的檔案[ulimit](https://ss64.com/bash/ulimit.html)設定為大於或等於`65536`的值，但您可以視需要使用較大的值。 您可以在命令列上設定限制，也可以將其設為使用者殼層的永久設定。

若要從命令列設定限制：

1. 切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
1. 將ulimit設為`65536`。

   ```bash
   ulimit -n 65536
   ```

若要在Bash shell中設定值：

1. 切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
1. 在文字編輯器中開啟`/home/<username>/.bashrc`。
1. 新增下列行：

   ```bash
   ulimit -n 65536
   ```

1. 儲存您對`.bashrc`檔案所做的變更，並結束文字編輯器。

>[!IMPORTANT]
>
>建議您避免在`pcre.recursion_limit`檔案中設定`php.ini`屬性的值，因為這會產生未完成且無失敗通知的回覆。

## 確認cron工作正在執行

UNIX工作排程器`cron`對於日常Adobe Commerce作業至關重要。 它會排程重新索引、電子報、電子郵件和網站地圖。 數個功能至少需要一個cron工作以檔案系統擁有者的身分執行。

若要驗證您的cron作業是否已正確設定，請輸入以下命令作為檔案系統擁有者來檢查crontab：

>[!NOTE]
>
>crontab是負責執行cron作業的組態檔。

```bash
crontab -l
```

類似下列的結果應會顯示：

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

cron未執行的另一個症狀是管理員中的以下錯誤：

![系統訊息 — cron未執行](../../assets/upgrade-guide/cron-not-running.png)

若要檢視錯誤，請按一下視窗頂端的&#x200B;**系統訊息**，如下所示：

![系統訊息通知](../../assets/upgrade-guide/system-messages.png)

如需詳細資訊，請參閱[設定並執行cron](../../configuration/cli/configure-cron-jobs.md)。

## 設定DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4包含安全性增強功能，需要將部分資料從序列化轉換為JSON。 此轉換會在升級期間發生，並且可能需要很長的時間，具體取決於資料庫中的資料量。

下清單格受到的影響最大：

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

如果您有大量資料，可以設定環境變數`DATA_CONVERTER_BATCH_SIZE`的值來改善效能。 預設值設為`50,000`。

若要設定環境變數：

1. 切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
1. 設定變數：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE`需要記憶體；請避免在未先測試的情況下將其設定為較大的值（約1 GB）。

1. 升級完成後，您可以取消設定變數：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 驗證檔案系統許可權

基於安全性理由，Adobe Commerce需要檔案系統的特定許可權。 許可權與&#x200B;_[所有權](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_&#x200B;不同。 擁有權決定誰可以在檔案系統上執行動作；許可權決定使用者可以執行的動作。

檔案系統中的目錄必須可由[檔案系統擁有者的](../../installation/prerequisites/file-system/overview.md)群組寫入。

若要確認您的檔案系統許可權已正確設定，請登入應用程式伺服器或使用您的託管提供者的檔案管理員應用程式。

例如，如果應用程式安裝在`/var/www/html/magento2`中，請輸入下列命令：

```bash
ls -l /var/www/html/magento2
```

範例輸出：

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

* 大部分的檔案是`-rw-rw----`，也就是`660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* 檔案系統擁有者是`magento_user`

若要取得詳細資訊，您可以輸入下列指令：

```bash
ls -la /var/www/html/magento2/pub
```

由於Adobe Commerce會將靜態檔案資產部署至`pub`的子目錄，因此也建議您在該處驗證許可權和擁有權。

如需詳細資訊，請參閱[檔案系統許可權和擁有權](../../installation/prerequisites/file-system/overview.md)。

## 設定`pub/`目錄根目錄

如需詳細資訊，請參閱[修改docroot以提高安全性](../../installation/tutorials/docroot.md)。

## 安裝撰寫器更新外掛程式

[`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer外掛程式解析了在更新為新產品需求之前必須對根專案`composer.json`檔案進行的變更。

外掛程式會識別並協助您解決相依性衝突，而非要求您手動識別及修正衝突，進而部分自動化手動升級。

若要安裝外掛程式：

1. 將套件新增至您的`composer.json`檔案。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 更新相依性：

   ```bash
   composer update
   ```
