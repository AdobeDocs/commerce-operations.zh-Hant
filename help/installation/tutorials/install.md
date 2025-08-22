---
title: 安裝Adobe Commerce
description: 請依照下列步驟，在您擁有的基礎設施上安裝Adobe Commerce。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '2093'
ht-degree: 0%

---

# 安裝Adobe Commerce

開始之前，請完成下列步驟：

* 確認您的系統符合[系統需求](../system-requirements.md)中討論的需求。

* 完成所有[先決條件](../prerequisites/overview.md)工作。

* 完成第一個安裝步驟。 請參閱[您的安裝或升級路徑](../overview.md)。

* 在您登入應用程式伺服器後，[切換到檔案系統擁有者](../prerequisites/file-system/overview.md)。

* 檢閱[開始使用命令列安裝](../composer.md)概覽。

>[!NOTE]
>
>您必須從其`bin`子目錄安裝應用程式。

您可以使用不同的選項多次執行安裝程式，以完成如下的安裝工作：

* 分階段安裝 — 例如，在為Secure Sockets Layer (SSL)設定Web伺服器後，您可以再次執行安裝程式來設定SSL選項。

* 更正先前安裝中的錯誤。

* 在其他資料庫執行處理中安裝應用程式。

>[!NOTE]
>
>如果您在相同資料庫執行個體中安裝Commerce軟體，預設情況下安裝程式不會覆寫資料庫。 您可以使用選用的`cleanup-database`引數來變更此行為。

另請參閱[更新、重新安裝、解除安裝](uninstall.md)。

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 安裝程式說明命令

您可以執行下列命令來尋找某些必要引數的值：

| 安裝程式引數 | 命令 |
| ------------------ | ------------------------------- |
| 語言 | `magento info:language:list` |
| 貨幣 | `magento info:currency:list` |
| 時區 | `magento info:timezone:list` |

>[!NOTE]
>
>如果執行這些命令時顯示錯誤，請確認您已更新安裝相依性，如[更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)中所述。

## 從命令列安裝

install指令會使用以下格式：

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

下表說明安裝選項名稱和值，例如安裝命令。 請參閱[範例localhost安裝](#sample-localhost-installations)。

>[!NOTE]
>
>包含空格或特殊字元的任何選項都必須用單引號或雙引號括住。

**管理員認證：**

下列選項指定管理員使用者的使用者資訊和認證。

在Adobe Commerce 2.2.8版及更新版本中，您可以在安裝期間或之後建立管理員使用者。 如果您在安裝期間建立使用者，則需要所有管理員認證變數。 請參閱[範例localhost安裝](#sample-localhost-installations)。

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員使用者的名字。 | 是 |
| `--admin-lastname` | 管理員使用者的姓氏。 | 是 |
| `--admin-email` | 管理員使用者的電子郵件地址。 | 是 |
| `--admin-user` | 管理員使用者名稱。 | 是 |
| `--admin-password` | 管理員使用者密碼。 密碼長度必須至少為7個字元，且必須至少包含一個字母和至少一個數字字元。 我們建議使用更長、更複雜的密碼。 以單引號括住整個密碼字串。 例如， `--admin-password='A0b9%t3g'` | 是 |

**站台和資料庫組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--base-url` | 用於以下列任何格式存取管理員和店面的基底URL：<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：**&#x200B;配置(http://或https://)和結尾斜線都是必要的。<br><br>`<your install dir>`是安裝應用程式的docroot相對路徑。 根據您設定網頁伺服器和虛擬主機的方式，路徑可能是magento2或可能為空白。<br><br>若要存取localhost上的應用程式，您可以使用`http://127.0.0.1/<your install dir>/`或`http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}`，代表虛擬主機設定或Docker等虛擬化環境所定義的基底URL。 例如，若您以主機名稱commerce.example.com設定虛擬主機，則可以以`--base-url={{base_url}}`安裝應用程式，並以`http://commerce.example.com/admin`之類的URL存取管理員。 | 是 |
| `--backend-frontname` | 用於存取管理員的統一資源識別碼(URI)。 您可以省略此引數，讓應用程式為您產生隨機URI，其模式如下： <code>admin_jkhgdfq</code>。<br><br>基於安全考量，建議您使用隨機URI。 對於駭客或惡意軟體而言，隨機URI更難被利用。<br><br>URI會在安裝結束時顯示。 您稍後隨時可以使用`magento info:adminuri`命令來顯示。<br><br>如果您選擇輸入值，建議您不要使用admin、backend等常見字詞。 管理員URI只能包含英數字元和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一項：<br><br> — 資料庫伺服器的完整主機名稱或IP位址。<br><br>- `localhost` （預設）或`127.0.0.1` （若您的資料庫伺服器與web伺服器位於相同的主機上）。localhost表示MySQL使用者端程式庫使用UNIX通訊端連線到資料庫。 `127.0.0.1`導致使用者端資料庫使用TCP通訊協定。 如需通訊端的詳細資訊，請參閱[PHP PDO_MYSQL檔案](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注意：**&#x200B;您可以選擇在其主機名稱中指定資料庫伺服器連線埠，例如www.example.com:9000 | 是 |
| `--db-name` | 您要安裝資料庫表格的資料庫執行處理名稱。<br><br>預設為`magento2`。 | 是 |
| `--db-user` | 資料庫執行處理擁有者的使用者名稱。<br><br>預設為`root`。 | 是 |
| `--db-password` | 資料庫執行處理擁有者的密碼。 | 是 |
| `--db-prefix` | 只有在您要在已經有Adobe Commerce表格的資料庫執行個體中安裝資料庫表格時才使用。<br><br>在這種情況下，請使用前置字元來識別此安裝的資料表。 有些客戶在含有相同資料庫中所有表格的伺服器上執行多個Adobe Commerce執行個體。<br><br>首碼的長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和下劃線字元。<br><br>此選項可讓這些客戶共用一個以上安裝的資料庫伺服器。 | 否 |
| `--db-ssl-key` | 使用者端金鑰的路徑。 | 否 |
| `--db-ssl-cert` | 使用者端憑證的路徑。 | 否 |
| `--db-ssl-ca` | 伺服器憑證的路徑。 | 否 |
| `--language` | 在管理員和店面中使用的語言代碼。 （如果您尚未這樣做，您可以從bin目錄輸入`magento info:language:list`來檢視語言代碼清單。） | 否 |
| `--currency` | 店面中使用的預設貨幣。 （如果尚未這樣做，您可以從bin目錄輸入`magento info:currency:list`來檢視貨幣清單。） | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 （如果尚未這樣做，您可以從bin目錄輸入`magento info:timezone:list`來檢視時區清單。） | 否 |
| `--use-rewrites` | `1`表示您對店面和管理程式中產生的連結使用網頁伺服器重寫。<br><br>`0`停用網頁伺服器重寫的使用。 這是預設值。 | 否 |
| `--use-secure` | `1`允許在店面URL中使用安全通訊端層(SSL)。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`停用使用SSL。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 安全基底URL，用於以下列格式存取您的管理員和店面： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1`表示您使用SSL來存取管理員。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`表示您沒有使用SSL與管理員。 這是預設值。 | 否 |
| `--admin-use-security-key` | 1會使得應用程式使用隨機產生的索引鍵值來存取管理員和表單中的頁面。 這些金鑰值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br><br>`0`停用金鑰。 | 否 |
| `--session-save` | 使用下列任一項： <br><br>- `db`將工作階段資料儲存在資料庫中。 如果您有叢集資料庫，請選擇資料庫儲存體；否則，與檔案式儲存體相比，可能不會有多大好處。<br><br>- `files`將工作階段資料儲存在檔案系統中。 除非檔案系統存取緩慢、您有叢集資料庫，或您想要將工作階段資料儲存在Redis中，否則檔案式工作階段儲存體是適當的。<br><br>- `redis`以將工作階段資料儲存在Redis。 如果您使用Redis作為預設或頁面快取，則必須已安裝Redis。 如需設定對Redis支援的其他資訊，請參閱使用工作階段儲存體的Redis 。 | 否 |
| `--key` | 如果您有金鑰，請指定金鑰以加密資料庫中的敏感資料。 如果您沒有，應用程式會為您產生一個。 | 是 |
| `--cleanup-database` | 若要在安裝應用程式之前刪除資料庫表格，請指定此引數，不要使用值。 否則，資料庫將保持不變。 | 否 |
| `--db-init-statements` | 進階MySQL設定引數。 在連線到MySQL資料庫時，使用資料庫初始化陳述式來執行。 在設定任何值之前，請查閱與此類似的參考。<br><br>預設為`SET NAMES utf8;`。 | 否 |
| `--sales-order-increment-prefix` | 指定字串值做為銷售訂單的前置詞。 通常，這是用來保證付款處理程式的唯一訂單編號。 | 否 |

>[!TIP]
>
>若要在安裝期間啟用遠端儲存服務，請參閱[設定指南](../../configuration/remote-storage/remote-storage.md)中的&#x200B;_設定遠端儲存_。

**搜尋引擎組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--search-engine` | 搜尋引擎的版本。 可能的值為`elasticsearch7`、`elasticsearch6`和`elasticsearch5`。 預設值為`elasticsearch7`。 如果您已安裝OpenSearch做為搜尋引擎，請指定值`elasticsearch7`。 Elasticsearch 5已過時，不建議使用。 | 否 |
| `--elasticsearch-host` | 執行搜尋引擎的主機名稱或IP位址。 預設值為`localhost`。 | 否 |
| `--elasticsearch-port` | 傳入HTTP要求的連線埠。 預設值為`9200`。 | 否 |
| `--elasticsearch-index-prefix` | 識別搜尋索引的前置詞。 預設值為`magento2`。 | 否 |
| `--elasticsearch-timeout` | 系統逾時前的秒數。 預設值為`15`。 | 否 |
| `--elasticsearch-enable-auth` | 啟用搜尋引擎伺服器上的驗證。 預設值為`false`。 | 否 |
| `--elasticsearch-username` | 用於驗證的使用者ID | 否，除非啟用驗證 |
| `--elasticsearch-password` | 用於驗證的密碼 | 否，除非啟用驗證 |

**[!DNL RabbitMQ]組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--amqp-host` | 請勿使用`--amqp`選項，除非您已設定[!DNL RabbitMQ]的安裝。 請參閱[!DNL RabbitMQ]安裝，以取得有關安裝和設定[!DNL RabbitMQ]的詳細資訊。<br><br>安裝[!DNL RabbitMQ]的主機名稱。 | 否 |
| `--amqp-port` | 用來連線到[!DNL RabbitMQ]的連線埠。 預設值為5672。 | 否 |
| `--amqp-user` | 連線到[!DNL RabbitMQ]的使用者名稱。 不要使用預設使用者`guest`。 | 否 |
| `--amqp-password` | 連線到[!DNL RabbitMQ]的密碼。 不要使用預設密碼`guest`。 | 否 |
| `--amqp-virtualhost` | 連線至[!DNL RabbitMQ]的虛擬主機。 預設值為`/`。 | 否 |
| `--amqp-ssl` | 指示是否要連線到[!DNL RabbitMQ]。 預設值為`false`。 如需為[!DNL RabbitMQ]設定SSL的相關資訊，請參閱[!DNL RabbitMQ]。 | 否 |
| `--consumers-wait-for-messages` | 消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否 | 否 |

**遠端儲存選項：**

| 名稱 | 說明 | 必填？ |
|--- |--- |--- |
| `remote-storage-driver` | 介面卡名稱<br>可能的值： <br>**檔案**：停用遠端儲存體並使用本機檔案系統&#x200B;<br>**aws-s3**：使用[Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | 否 |
| `remote-storage-bucket` | 物件儲存或容器名稱 | 否 |
| `remote-storage-prefix` | 選擇性首碼（物件儲存內的位置） | 否 |
| `remote-storage-region` | 區域名稱 | 否 |
| `remote-storage-key` | 選用的存取金鑰 | 否 |
| `remote-storage-secret` | 選擇性秘密金鑰 | 否 |

**鎖定組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供者名稱。<br><br>可用的鎖定提供者： `db`、`zookeeper`、`file`。<br><br>預設鎖定提供者： `db` | 否 |
| `--lock-db-prefix` | 使用`db`鎖定提供者時，避免鎖定衝突的特定資料庫首碼。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用`zookeeper`鎖定提供者時，要連線至Zookeeper叢集的主機與連線埠。<br><br>例如： `127.0.0.1:2181` | 是，如果您設定`--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper儲存鎖定的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 儲存檔案鎖定的路徑。 | 是，如果您設定`--lock-provider=file` |

**消費者組態選項：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>若要在安裝應用程式後啟用或停用模組，請參閱[啟用和停用模組](manage-modules.md)。

**敏感資料：**

{{$include /help/_includes/sensitive-data.md}}

### localhost安裝範例

下列範例顯示使用各種選項在本機安裝Adobe Commerce的命令。

#### 範例1 — 使用管理員使用者帳戶進行基本安裝

下列範例會安裝具有以下選項的應用程式：

* 應用程式安裝在`magento2`上相對於Web伺服器docroot的`localhost`目錄中，而且管理員的路徑是`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於相同的主機上。

  資料庫名稱為`magento`，使用者名稱和密碼均為`magento`

* 使用伺服器重寫

* 管理員具有下列屬性：

   * 名字和姓氏為`Commerce User`
   * 使用者名稱是`admin`，密碼是`admin123`
   * 電子郵件地址為`user@example.com`

* 預設語言為`en_US` （美式英文）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* Elasticsearch 7已安裝在`es-host.example.com`上，並連線到連線埠9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

類似下列顯示以指示成功安裝的訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 範例2 — 沒有管理員使用者帳戶的基本安裝

您可以安裝應用程式，而不需建立管理員使用者，如下列範例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

如果安裝成功，會顯示類似下列的訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安裝後，您可以使用`admin:user:create`命令建立管理員使用者：
[建立或編輯管理員](admin.md#create-or-edit-an-administrator)

#### 範例3 — 使用其他選項安裝

下列範例會安裝具有以下選項的應用程式：

* Magapplication安裝在`magento2`上相對於Web伺服器docroot的`localhost`目錄中，且管理員的路徑為`admin`；因此：

  您的店面URL是`http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於相同的主機上。

  資料庫名稱為`magento`，使用者名稱和密碼均為`magento`

* 管理員具有下列屬性：

   * 名字和姓氏為`Commerce User`
   * 使用者名稱是`admin`，密碼是`admin123`
   * 電子郵件地址為`user@example.com`

* 預設語言為`en_US` （美式英文）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* 安裝程式先清除資料庫，再安裝資料表和綱要
* 您使用`ORD$`銷售訂單增量前置詞（由於它包含特殊字元[`$`]，因此值必須用雙引號括住）
* 工作階段資料儲存在資料庫中
* 使用伺服器重寫
* Elasticsearch 7已安裝在`es-host.example.com`上，並連線到連線埠9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>您必須在單行中輸入命令，或如前例所示，每行結尾必須有`\`個字元。

如果安裝成功，會顯示類似下列的訊息：

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>如果您有一個使用者帳戶可存取應用程式伺服器，請參閱[設定umask](../next-steps/set-umask.md)。 此類設定是共用託管的典型設定。

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
