---
title: 進階內部部署安裝
description: 瞭解您擁有的基礎架構上 Adobe Systems Commerce 的高級安裝方案。
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 0%

---

# 進階本地安裝

>[!TIP]
>
>遺失？ 需要協助嗎？ 請嘗試我們的[快速入門安裝](composer.md)或[貢獻者安裝](https://developer.adobe.com/commerce/contributor/guides/install/)指南。

>[!NOTE]
>
>如果您選擇啟用SELinux，請參閱[SELinux和iptables](prerequisites/security.md)。

## 命令列介面(CLI)

Adobe Commerce有一個用於安裝和設定工作的單一命令列介面： `<magento_root>/bin/magento`。 介面會執行多項工作，包括：

* 安裝（以及建立或更新資料庫架構、建立部署組態等相關工作）。
* 正在清除快取。
* 管理索引，包括重新索引。
* 建立翻譯字典和翻譯套件。
* 為外掛程式產生不存在的類別（例如處理站和攔截器），為物件管理員產生相依性插入組態。
* 部署靜態檢視檔案。
* 從較少專案建立CSS。

其他優點：

* 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和組態命令。
* 以Symfony為基礎的一致使用者介面。
* CLI可擴充，因此協力廠商開發人員可以「插入」至其中。 這還有消除使用者學習曲線的額外好處。
* 已停用模組的命令不顯示。

本主題說明如何使用CLI安裝Adobe Commerce軟體。 如需設定的相關資訊，請參閱[設定指南](../configuration/overview.md)。

安裝程式可多次執行（如有必要），因此您可以：

* 提供不同的值

  例如，在為Secure Sockets Layer (SSL)設定Web伺服器後，您可以執行安裝程式來設定SSL選項。

* 更正先前安裝中的錯誤
* 在其他資料庫執行個體中安裝Adobe Commerce

## 開始安裝之前

開始之前，請完成下列步驟：

* 驗證您的系統是否滿足系統要求](system-requirements.md)中[討論的要求。

* 完整應用程式所有 [先決條件](prerequisites/overview.md) 工作。

* 完整應用程式第一個安裝步驟。 請參閱 [您的安裝或升級路徑](overview.md)。

* 登錄到 應用程式 伺服器后， [切換到文件系統擁有者](prerequisites/file-system/overview.md)。

* 檢閱[安裝快速入門](composer.md)概述。

>[!NOTE]
>
>您必須從`bin`子目錄安裝Adobe Commerce。

您可以使用不同的選項多次執行安裝程式，以完成如下的安裝工作：

* 分階段安裝 — 例如，在為Secure Sockets Layer (SSL)設定Web伺服器之後，您可以再次執行安裝程式來設定SSL選項。

* 更正先前安裝中的錯誤。

* 在其他資料庫執行個體安裝 Adobe Systems Commerce。

>[!NOTE]
>
>依照預設，如果您在相同資料庫執行個體中安裝軟體，安裝程式不會覆寫資料庫。 您可以使用選用的`cleanup-database`引數來變更此行為。

另請參閱[更新、重新安裝、解除安裝](tutorials/uninstall.md)。

### 安全安裝

{{$include /help/_includes/secure-install.md}}

## 安裝程式說明命令

您可以執行以下命令來尋找某些所需參數的值：

| 安裝程式引數 | 命令 |
| ------------------ | ------------------------------- |
| 語言 | `bin/magento info:language:list` |
| 貨幣 | `bin/magento info:currency:list` |
| 時區 | `bin/magento info:timezone:list` |

>[!NOTE]
>
>如果執行這些命令時顯示錯誤，請確認您已更新安裝相依性，如[更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)中所述。

## 從命令列安裝

install指令會使用以下格式：

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

下表說明安裝選項名稱和值。 如需安裝命令的範例，請參閱[範例localhost安裝](#sample-localhost-installations)。

>[!NOTE]
>
>包含空格或特殊字元的任何選項都必須用單引號或雙引號括住。

**管理員認證：**

下列選項指定管理員使用者的使用者資訊和認證。

您可以在安裝期間或安裝後建立「管理員」使用者。 如果您在安裝期間建立使用者，則需要所有管理員認證變數。 請參閱[範例localhost安裝](#sample-localhost-installations)。

下清單格提供許多（但並非全部）可用的安裝引數。 如需完整清單，請參閱[命令列工具參考](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises)。

| 名字 | 價值 | 必填？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員使用者的名字。 | 是 |
| `--admin-lastname` | 管理員使用者的姓氏。 | 是 |
| `--admin-email` | 管理員使用者的電子郵件地址。 | 是 |
| `--admin-user` | 管理員使用者名稱。 | 是 |
| `--admin-password` | 管理員使用者密碼。 密碼長度必須至少為7個字元，且必須至少包含一個字母和至少一個數字字元。 我們建議使用更長、更複雜的密碼。 以單引號括住整個密碼字串。 例如， `--admin-password='A0b9%t3g'` | 是 |

**站台和資料庫組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--base-url` | 用於以下列任何格式存取管理員和店面的基底URL：<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：**&#x200B;配置(http://或https://)和結尾斜線都是必要的。<br><br>`<your install dir>`是安裝Adobe Commerce軟體的docroot相對路徑。 根據您設定網頁伺服器和虛擬主機的方式，路徑可能是magento2或可能為空白。<br><br>存取Adobe Commerce或MagenAdobe Commerceuse `http://127.0.0.1/<your install dir>/`或`http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}`，代表虛擬主機設定或Docker等虛擬化環境所定義的基底URL。 例如，如果您設定主機名稱為`magento.example.com`的虛擬主機，則可以使用`--base-url={{base_url}}`安裝軟體，並以`http://magento.example.com/admin`之類的URL存取管理員。 | 是 |
| `--backend-frontname` | 用於存取管理員的統一資源識別碼(URI)。 您可以省略此引數，讓應用程式為您產生隨機URI，其模式如下： <code>admin_jkhgdfq</code>.<br><br>基於安全考量，建議您使用隨機URI。 對於駭客或惡意軟體而言，隨機URI更難被利用。<br><br>URI 將顯示在安裝結束時。 您稍後隨時可以使用`bin/magento info:adminuri`命令來顯示。<br><br>如果您選擇輸入值，我們建議您不要使用按讚 admin、backend 的常用詞。 管理 URI 只能包含字母數位值和下劃線字元 （`_`）。 | 不 |
| `--db-host` | 使用以下任一方法：<br><br>- 資料庫伺服器的完全限定主機名或IP位址。<br><br>- `localhost` （預設）或者 `127.0.0.1` 如果您的資料庫伺服器與 Web 伺服器位於同一主機.localhost 表示使用 UNIX 套接字連接到資料庫的 MySQL 用戶端資料庫。 `127.0.0.1` 導致用戶端資料庫使用 TCP 協定。 有關套接字的更多資訊，請參閱 [PHP PDO_MYSQL 文件](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注意：**&#x200B;您可以選擇在其主機名稱中指定資料庫伺服器連線埠，例如www.example.com:9000 | 是的 |
| `--db-name` | 要在其中安裝資料庫表的資料庫執行個體的名稱。<br><br>預設為 `magento2`。 | 是的 |
| `--db-user` | 資料庫執行處理擁有者的使用者名稱。<br><br>預設為`root`。 | 是 |
| `--db-password` | 資料庫執行處理擁有者的密碼。 | 是的 |
| `--db-prefix` | 僅當在已包含 Commerce 表的資料庫執行個體中安裝資料庫表時Adobe Systems才使用。<br><br>在這種情況下，請使用前綴來標識此安裝的表。 有些客戶擁有多個 Adobe Systems Commerce 或 MagenAdobe Commerceserver，且所有表格都位於同一個資料庫中。<br><br>前綴的長度最多為5個字元。 它必須以字母開頭，並且只能包含字母、數字和下劃線字元。<br><br>此選項可讓這些客戶共用一個以上Adobe Commerce安裝的資料庫伺服器 |
| `--db-ssl-key` | 使用者端金鑰的路徑。 | 否 |
| `--db-ssl-cert` | 使用者端憑證的路徑。 | 否 |
| `--db-ssl-ca` | 伺服器憑證的路徑。 | 否 |
| `--language` | 在管理員和店面中使用的語言代碼。 （如果您尚未這樣做，您可以從bin目錄輸入`bin/magento info:language:list`來檢視語言代碼清單。） | 否 |
| `--currency` | 店面中使用的預設貨幣。 （如果尚未這樣做，您可以從bin目錄輸入`bin/magento info:currency:list`來檢視貨幣清單。） | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 （如果您尚未這樣做，您可以從`bin/`目錄輸入`bin/magento info:timezone:list`來檢視時區清單。） | 否 |
| `--use-rewrites` | `1`表示您對店面和管理程式中產生的連結使用網頁伺服器重寫。<br><br>`0`停用網頁伺服器重寫的使用。 這是預設值。 | 不 |
| `--use-secure` | `1`允許在店面URL中使用安全通訊端層(SSL)。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`停用使用SSL。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 安全基底URL，用於以下列格式存取您的管理員和店面： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1`表示您使用SSL來存取管理員。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`表示您沒有使用SSL與管理員。 這是預設值。 | 否 |
| `--admin-use-security-key` | 1會使得應用程式使用隨機產生的索引鍵值來存取管理員和表單中的頁面。 這些金鑰值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br><br>`0`停用金鑰。 | 否 |
| `--session-save` | 使用下列任一項： <br><br>- `db`將工作階段資料儲存在資料庫中。 如果您有叢集資料庫，請選擇資料庫儲存體；否則，與檔案式儲存體相比，可能不會有多大好處。<br><br>- `files`將工作階段資料儲存在檔案系統中。 除非檔案系統存取緩慢、您有叢集資料庫，或您想要將工作階段資料儲存在Redis中，否則檔案式工作階段儲存體是適當的。<br><br>- `redis`以將工作階段資料儲存在Redis。 如果您使用Redis作為預設或頁面快取，則必須已安裝Redis。 如需設定對Redis支援的其他資訊，請參閱使用工作階段儲存體的Redis 。 | 否 |
| `--key` | 如果您有金鑰，請指定金鑰以加密資料庫中的敏感資料。 如果您沒有，應用程式會為您產生一個。 | 是 |
| `--cleanup-database` | 若要在安裝Adobe Commerce之前刪除資料庫表格，請指定此引數（不含值）。 否則，資料庫將保持不變。 | 不 |
| `--db-init-statements` | 進階 MySQL 配置參數。 使用資料庫初始化語句在連接到 MySQL 資料庫時運行。 在設置任何值之前，請查閱與此類似的參考。<br><br>預設為 `SET NAMES utf8;`。 | 不 |
| `--sales-order-increment-prefix` | 指定要用作銷售訂單前綴的字串值。 通常，這是用來保證付款處理程式的唯一訂單編號。 | 否 |

**搜尋引擎組態選項：**

| 名稱 | 價值 | 必填？ |
|--- |--- |--- |
| `--search-engine` | 要用作搜尋引擎的 Elasticsearch 或 OpenSearch 版本。 預設值 `elasticsearch7`為 。 Elasticsearch 5 已淘汰，不建議使用。 | 否 |
| `--elasticsearch-host` | 執行Elasticsearch的主機名稱或IP位址。 預設值為`localhost`。 | 否 |
| `--elasticsearch-port` | 傳入HTTP要求的Elasticsearch連線埠。 預設值 `9200`為 。 | 不 |
| `--elasticsearch-index-prefix` | 標識索引Elasticsearch搜尋的前綴。 預設值 `magento2`為 。 | 否 |
| `--elasticsearch-timeout` | 系統逾時前的秒數。 預設值為`15`。 | 否 |
| `--elasticsearch-enable-auth` | 啟用Elasticsearch伺服器上的驗證。 預設值 `false`為 。 | 不 |
| `--elasticsearch-username` | 向Elasticsearch伺服器驗證的使用者ID。 | 否，除非啟用驗證 |
| `--elasticsearch-password` | 向Elasticsearchserver進行驗證的密碼。 | 否，除非啟用驗證 |
| `--opensearch-host` | 執行OpenSearch的主機名稱或IP位址。 預設值為`localhost`。 | 否 |
| `--opensearch-port` | 傳入HTTP要求的OpenSearch連線埠。 預設值為`9200`。 | 否 |
| `--opensearch-index-prefix` | 識別OpenSearch搜尋索引的前置詞。 預設值為`magento2`。 | 不 |
| `--opensearch-timeout` | 系統逾時前的秒數。 預設值為`15`。 | 否 |
| `--opensearch-enable-auth` | 啟用OpenSearch伺服器上的驗證。 預設值為`false`。 | 否 |
| `--opensearch-username` | 用於向OpenSearch伺服器驗證的使用者ID。 | 否，除非啟用驗證 |
| `--opensearch-password` | 用於向OpenSearch伺服器驗證的密碼。 | 否，除非啟用驗證 |

**[!DNL RabbitMQ]組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--amqp-host` | 除非您已經設置了 的[!DNL RabbitMQ]安裝，否則不要使用這些`--amqp`選項。有關安裝和配置[!DNL RabbitMQ]的詳細資訊，請參閱[!DNL RabbitMQ]安裝。<br><br>安裝[!DNL RabbitMQ]的主機名稱。 | 否 |
| `--amqp-port` | 用來連線到[!DNL RabbitMQ]的連線埠。 預設值為5672。 | 不 |
| `--amqp-user` | 用於連接到 [!DNL RabbitMQ]的使用者名。 請勿使用預設用戶 `guest`。 | 不 |
| `--amqp-password` | 用於連接到 [!DNL RabbitMQ]密碼。 請勿使用預設密碼 `guest`。 | 不 |
| `--amqp-virtualhost` | 用于連接到 [!DNL RabbitMQ]的虛擬主機。 預設值 `/`為 。 | 不 |
| `--amqp-ssl` | 指示是否連線到 [!DNL RabbitMQ]。 預設值 `false`為 。 如需為[!DNL RabbitMQ]設定SSL的相關資訊，請參閱[!DNL RabbitMQ]。 | 否 |
| `--consumers-wait-for-messages` | 消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否 | 否 |

**鎖定設定選項：**

| 名字 | 價值 | 必填？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供者名稱。<br><br>可用的鎖定提供者： `db`、`zookeeper`、`file`。<br><br>預設鎖定提供者： `db` | 否 |
| `--lock-db-prefix` | 特定的資料庫前綴，以避免在使用 `db` 鎖定提供程式時發生鎖定衝突。<br><br>預設值： `NULL` | 不 |
| `--lock-zookeeper-host` | 主機和連接埠以在使用 `zookeeper` 鎖定提供程序時連接到 Zookeeper 群集。<br><br>例如： `127.0.0.1:2181` | 是，如果您將 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper儲存鎖定的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 儲存檔案鎖定的路徑。 | 是，如果您將 `--lock-provider=file` |

**使用者設定選項：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>若要在安裝Adobe Commerce之後啟用或停用模組，請參閱[啟用和停用模組](tutorials/manage-modules.md)。

**敏感資料：**

{{$include /help/_includes/sensitive-data.md}}

### localhost安裝範例

下列範例顯示使用各種選項在本機安裝Adobe Commerce的命令。

#### 範例1 — 使用管理員使用者帳戶進行基本安裝

下列範例會安裝包含下列選項的Adobe Commerce：

* 應用程式安裝在`localhost`上相對於Web伺服器docroot的`magento2`目錄中，而且管理員的路徑是`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於相同的主機上。

  資料庫名稱為`magento`，使用者名稱和密碼均為`magento`

* 使用伺服器重寫

* 管理員具有以下屬性：

   * 名字和姓氏為`Magento User`
   * 使用者名是 `admin` ，密碼是 `admin123`
   * 電子郵件位址是 `user@example.com`

* 預設語言為 `en_US` （美國英文）
* 默認貨幣為美元
* 預設時區為美國中部（美國/芝加哥）
* OpenSearch 1.2已安裝在`os-host.example.com`上，並連線到連線埠9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

類似下列顯示以指示成功安裝的訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 範例2 — 無管理員使用者帳戶的基本安裝

您可以安裝Adobe Commerce而不建立管理員使用者，如下列範例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

如果安裝成功，會顯示類似下列的訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安裝后，您可以使用以下命令創建 `admin:user:create` 管理用戶：
[建立或編輯管理員](tutorials/admin.md#create-or-edit-an-administrator)

#### 範例 3 - 使用其他選項安裝

下列範例使用下列選項安裝 Adobe Systems Commerce：

* 應用程式安裝在`localhost`上相對於Web伺服器docroot的`magento2`目錄中，而且管理員的路徑是`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 資料庫伺服器與 Web 伺服器位於同一主機上。

  資料庫名稱為 `magento`，使用者名和密碼均為 `magento`

* 管理員具有以下屬性：

   * 名字和姓氏是 `Magento User`
   * 使用者名是 `admin` ，密碼是 `admin123`
   * 電子郵件位址是 `user@example.com`

* 預設語言為 `en_US` （美國英文）
* 默認貨幣為美元
* 預設時區為美國中部（美國/芝加哥）
* 安裝程式首先清理資料庫，然後再安裝表和綱要
* 您可以使用銷售訂單增量前置詞`ORD$` （因為它包含特殊字元[`$`]，所以值必須用雙引號括住）
* 工作階段資料儲存在資料庫中
* 使用伺服器重寫
* OpenSearch已安裝在`os-host.example.com`上，並連線到連線埠9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>您必須在單行中輸入命令，或如前例所示，每行結尾必須有`\`個字元。

如果安裝成功，將顯示按讚下列訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
