---
title: 完成先決條件
description: 通過完成這些先決條件步驟，為升級準備您的Adobe Commerce或Magento Open Source項目。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# 完成升級先決條件

瞭解運行Adobe Commerce或Magento Open Source所需要的內容非常重要。 您必須首先查看 [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 版本。

在複查系統要求後，必須先完成以下先決條件，然後才能升級系統：

- 更新所有軟體
- 驗證是否安裝了Elasticsearch
- 設定開啟的檔案限制
- 驗證cron作業是否正在運行
- 設定 `DATA_CONVERTER_BATCH_SIZE`
- 驗證檔案系統權限
- 設定 `pub/` 目錄根目錄
- 安裝Composer更新插件

## 更新所有軟體

的 [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 準確描述哪些第三方軟體版本已通過Adobe Commerce和Magento Open Source版本的測試。

確保更新環境中的所有系統要求和依賴項。 參見PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), [所需的PHP設定](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set)。

## 驗證Elasticsearch是否已安裝

Adobe Commerce和Magento Open Source需要安裝Elasticsearch才能使用軟體。 在從2.3.x升級到2.4之前，必須檢查在2.3.x實例中是使用MySQL、Elasticsearch還是第三方擴展作為目錄搜索引擎。 結果決定了您必須做什麼 _先_ 升級到2.4。

您可以使用命令行或管理員來確定目錄搜索引擎：

- 輸入 `bin/magento config:show catalog/search/engine` 的子菜單。 該命令返回的值 `mysql`。 `elasticsearch` (表示已配置Elasticsearch2), `elasticsearch5`。 `elasticsearch6`。 `elasticsearch7`或自定義值，表示您已安裝第三方搜索引擎。

- 在管理員中，檢查 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 的子菜單。

以下各節介紹升級到2.4.0之前必須執行哪些操作。

### MySQL

從2.4開始，MySQL不再是受支援的目錄搜索引擎。 升級前必須安裝和配置Elasticsearch。 使用以下資源幫助您完成此過程：

- [安裝和配置Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 配置要使用的Elasticsearch [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) 或 [阿帕奇](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [將Commerce配置為使用Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 重新索引

一些第三方目錄搜索引擎在Adobe Commerce搜索引擎上運行。 聯繫您的供應商以確定您是否必須更新擴展。

### Elasticsearch

必須安裝和配置Elasticsearch，然後才能升級到2.4.0。Adobe不再支援Elasticsearch2.x、5.x和6.x。

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有關備份資料、檢測潛在遷移問題和在部署到生產之前測試升級的完整說明。 根據您當前版本的Elasticsearch，可能需要或不需要完全群集重新啟動。

Elasticsearch需要JDK 1.8或更高版本。 請參閱 [安裝Java軟體開發工具包(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 以檢查安裝的JDK版本。

[配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 描述將Elasticsearch2更新為支援的版本後必須執行的任務。

### 第三方擴展

我們建議您與搜索引擎供應商聯繫，以確定您的擴展是否與2.4完全相容。

## 設定開啟的檔案限制

設定開啟的檔案限制(ulimit)有助於避免因多次遞歸調用長查詢字串或使用 `bin/magento setup:rollback` 的子菜單。 此命令對於不同的UNIX外殼不同。 請參考您的個性化特點，瞭解 `ulimit` 的子菜單。

Adobe建議設定開啟的檔案 [上限](http://ss64.com/bash/ulimit.html) 值 `65536` 或更多，但必要時可以使用更大的值。 可以在命令行上設定ulimit ，也可以將其設定為用戶shell的永久設定。

要從命令行設定限制：

1. 切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 將上限設定為65536。

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > 開啟檔案ulimit的語法取決於您使用的UNIX shell。 前面的設定應與CentOS和Ubuntu一起使用Bash外殼。 但是，對於Mac作業系統，正確的設定是ulimit -S 65532。 有關詳細資訊，請參閱手冊頁或作業系統引用。

要在Bash外殼中設定值：

1. 切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 開啟 `/home/<username>/.bashrc` 的子菜單。
1. 添加以下行：

   ```bash
   ulimit -s 65536
   ```

1. 保存對 `.bashrc` 並退出文本編輯器。

>[!IMPORTANT]
>
>建議您避免為 `pcre.recursion_limit` 屬性 `php.ini` 檔案，因為它可能導致不完整的回滾，且沒有失敗通知。

## 驗證cron作業是否正在運行

UNIX任務計畫程式 `cron` 是日常Adobe Commerce和Magento Open Source運營的關鍵。 它會安排諸如重新編製索引、新聞通訊、電子郵件、小小集等。 若干功能要求至少以檔案系統所有者身份運行一個cron作業。

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

請參閱 [配置並運行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 的雙曲餘切值。

## 設定DATA_CONVERTER_BATCH_SIZE

Adobe Commerce2.4包含安全增強功能，要求將某些資料從序列化轉換為JSON。 此轉換在升級過程中發生，可能需要很長時間，具體取決於資料庫中有多少資料。

下表受影響最大：

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

如果您有大量資料，則可以通過設定環境變數的值來提高效能， `DATA_CONVERTER_BATCH_SIZE`。 預設情況下，值設定為 `50,000`。

要設定環境變數：

1. 切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 設定變數：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 需要記憶體；避免將其設定為大值（大約1GB），而不先進行測試。

1. 升級完成後，可以取消設定變數：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 驗證檔案系統權限

出於安全原因，Adobe Commerce和Magento Open Source需要對檔案系統具有某些權限。 權限與 _[所有權](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_。 所有權決定誰可以對檔案系統執行操作；權限決定用戶可以做什麼。

檔案系統中的目錄必須由 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) 組。

要驗證是否正確設定了檔案系統權限，請登錄到應用程式伺服器或使用托管提供程式的檔案管理器應用程式。

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

- 大多數檔案 `-rw-rw----`，即 `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- 檔案系統所有者是 `magento_user`

要獲取更多詳細資訊，可以輸入以下命令：

```bash
ls -la /var/www/html/magento2/pub
```

因為Adobe Commerce和Magento Open Source將靜態檔案資產部署到 `pub`，驗證權限和所有權也是一個好主意。

有關詳細資訊，請參見 [檔案系統權限和所有權](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。

## 設定 `pub/` 目錄根目錄

請參閱 [修改docroot以提高安全性](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) 的子菜單。

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
