---
title: 高級內部部署安裝
description: 了解Adobe Commerce的進階安裝案例，或Magento Open Source您擁有的基礎架構。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '2339'
ht-degree: 0%

---


# 高級內部部署安裝

>[!TIP]
>
>迷路了？ 需要幫手嗎？ 試試我們的 [快速入門安裝](composer.md) 或 [貢獻者安裝](https://developer.adobe.com/commerce/contributor/guides/install/) 指南。

>[!NOTE]
>
>如果選擇啟用SELinux，請參閱 [SELinux和iptables](prerequisites/security.md).

## 命令行介面(CLI)

Adobe Commerce和Magento Open Source有單一命令列介面，可執行安裝和設定任務： `<magento_root>/bin/magento`. 介面執行多項任務，包括：

* 安裝（以及相關任務，如建立或更新資料庫架構、建立部署配置）。
* 清除快取。
* 管理索引，包括重新索引。
* 建立翻譯字典和翻譯套件。
* 生成不存在的類，如工廠和插件的截取器，為對象管理器生成依賴項注入配置。
* 部署靜態視圖檔案。
* 從更少建立CSS。

其他好處：

* 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和配置命令。
* 基於Symfony的一致用戶介面。
* CLI是可擴充的，因此協力廠商開發人員可以「外掛」CLI。 這還有消除用戶學習曲線的額外好處。
* 禁用模組的命令不顯示。

本主題討論如何使用CLI安裝Adobe Commerce或Magento Open Source軟體。 如需設定的相關資訊，請參閱 [配置指南](../configuration/overview.md).

如有必要，安裝程式可執行多次，因此您可以：

* 提供不同的值

   例如，為安全套接字層(SSL)配置Web伺服器後，可以運行安裝程式來設定SSL選項。

* 更正以前安裝中的錯誤
* 在不同的資料庫執行個體中安裝Adobe Commerce或Magento Open Source

## 開始安裝之前

開始之前，請完成下列步驟：

* 驗證您的系統是否滿足 [系統需求](system-requirements.md).

* 全部完成 [先決條件](prerequisites/overview.md) 任務。

* 完成第一個安裝步驟。 請參閱 [您的安裝或升級路徑](overview.md).

* 登入應用程式伺服器後， [切換到檔案系統所有者](prerequisites/file-system/overview.md).

* 檢閱 [安裝快速入門](composer.md) 概述。

>[!NOTE]
>
>您必須從以下位置安裝Adobe Commerce或Magento Open Source: `bin` 子目錄。

您可以使用不同選項多次運行安裝程式以完成如下安裝任務：

* 分階段安裝 — 例如，為安全套接字層(SSL)配置Web伺服器後，可以再次運行安裝程式以設定SSL選項。

* 更正以前安裝中的錯誤。

* 在不同的資料庫執行個體中安裝Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>預設情況下，如果在同一資料庫實例中安裝軟體，則安裝程式不會覆蓋資料庫。 您可以使用 `cleanup-database` 參數來變更此行為。

另請參閱 [更新、重新安裝、卸載](tutorials/uninstall.md).

### 安全安裝

{{$include /help/_includes/secure-install.md}}

## 安裝程式幫助命令

您可以執行下列命令，以尋找某些必要引數的值：

| 安裝程式引數 | 命令 |
| ------------------ | ------------------------------- |
| 語言 | bin/magento資訊:language:清單 |
| 貨幣 | bin/magento資訊:currency:清單 |
| 時區 | bin/magento資訊:timezone:清單 |

>[!NOTE]
>
>如果運行這些命令時顯示錯誤，請驗證是否更新了安裝依賴項，如 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 從命令列安裝

install命令使用以下格式：

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

下表說明了安裝選項的名稱和值。 例如，安裝命令，請參見 [本地主機安裝示例](#sample-localhost-installations).

>[!NOTE]
>
>任何包含空格或特殊字元的選項都必須以單引號或雙引號括住。

**管理員憑證：**

以下選項指定管理員用戶的用戶資訊和憑據。

您可以在安裝期間或之後建立管理員使用者。 如果您在安裝期間建立使用者，則需要所有管理員憑證變數。 請參閱 [本地主機安裝示例](#sample-localhost-installations).

下表提供許多但並非所有可用的安裝參數。 如需完整清單，請參閱 [命令行工具參考](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員用戶的名字。 | 是 |
| `--admin-lastname` | 管理員用戶的姓氏。 | 是 |
| `--admin-email` | 管理員用戶的電子郵件地址。 | 是 |
| `--admin-user` | 管理員用戶名。 | 是 |
| `--admin-password` | 管理員用戶密碼。 密碼長度必須至少為7個字元，並且必須至少包含一個字母和至少一個數字字元。 我們建議使用更長、更複雜的密碼。 以單引號括住整個密碼字串。 例如， `--admin-password='A0b9%t3g'` | 是 |

**站點和資料庫配置選項：**

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--base-url` | 以下列任何格式用來存取管理員和店面的基本URL:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 配置(http://或https://)和尾斜線都是必要項目。<br><br>`<your install dir>` 是用來安裝Adobe Commerce或Magento Open Source軟體的相對路徑。 視您設定Web伺服器和虛擬主機的方式而定，路徑可能是magento2，也可能是空白的。<br><br>若要在localhost上存取Adobe Commerce或Magento Open Source，您可以使用 `http://127.0.0.1/<your install dir>/` 或 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 它表示由虛擬主機設定或虛擬化環境（如Docker）定義的基本URL。 例如，如果您設定了主機名稱為的虛擬主機 `magento.example.com`，您可以使用 `--base-url={{base_url}}` 並使用URL(如 `http://magento.example.com/admin`. | 是 |
| `--backend-frontname` | 統一資源標識符(URI)以訪問管理員。 您可以忽略此參數，讓應用程式為您產生隨機URI，其模式如下： admin_jkhgdfq</code>.<br><br>我們建議使用隨機URI以用於安全目的。 隨機URI對於駭客或惡意軟體來說更難以利用。<br><br>URI在安裝結束時顯示。 您隨時可以使用 `bin/magento info:adminuri` 命令。<br><br>如果您選擇輸入值，建議您不要使用管理、後端等常見字詞。 管理URI可包含英數字元值和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一項：<br><br> — 資料庫伺服器的完全限定主機名或IP地址。<br><br>- `localhost` （預設）或 `127.0.0.1` 如果資料庫伺服器與web伺服器位於同一主機上。localhost表示MySQL客戶端庫使用UNIX套接字連接到資料庫。 `127.0.0.1` 導致客戶端庫使用TCP協定。 有關套接字的詳細資訊，請參見 [PHP PDO_MYSQL文檔](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 可以選擇在其主機名中指定資料庫伺服器埠，如www.example.com:9000 | 是 |
| `--db-name` | 要安裝資料庫表的資料庫實例的名稱。<br><br>預設為 `magento2`. | 是 |
| `--db-user` | 資料庫實例所有者的用戶名。<br><br>預設為 `root`. | 是 |
| `--db-password` | 資料庫實例所有者的密碼。 | 是 |
| `--db-prefix` | 僅當在已有Adobe Commerce或Magento Open Source表的資料庫實例中安裝資料庫表時，才使用。<br><br>在這種情況下，請使用前置詞來標識此安裝的表。 有些客戶在伺服器上執行多個Adobe Commerce或Magento Open Source執行個體，且同一資料庫中的所有表格皆在其中。<br><br>前置詞長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和底線字元。<br><br>此選項允許這些客戶與多個Adobe Commerce或Magento Open Source安裝共用資料庫伺服器。 | 否 |
| `--db-ssl-key` | 客戶端密鑰的路徑。 | 否 |
| `--db-ssl-cert` | 客戶端證書的路徑。 | 否 |
| `--db-ssl-ca` | 伺服器憑證的路徑。 | 否 |
| `--language` | 要在管理員和店面中使用的語言代碼。 (如果您尚未這麼做，您可以輸入 `bin/magento info:language:list` （從bin目錄）。 | 否 |
| `--currency` | 要在店面中使用的預設貨幣。 (如果您尚未這麼做，您可以輸入 `bin/magento info:currency:list` （從bin目錄）。 | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 (如果您尚未這麼做，您可以輸入 `bin/magento info:timezone:list` 從 `bin/` 目錄。) | 否 |
| `--use-rewrites` | `1` 表示您在storefront和「管理員」中，對產生的連結使用web伺服器重寫。<br><br>`0` 禁用web伺服器重寫的使用。 這是預設值。 | 否 |
| `--use-secure` | `1` 允許在店面URL中使用安全套接字層(SSL)。 選取此選項之前，請確定您的Web伺服器支援SSL。<br><br>`0` 停用SSL的使用。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 以下列格式用來存取管理員和店面的安全基本URL: `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL存取管理員。 選取此選項之前，請確定您的Web伺服器支援SSL。<br><br>`0` 表示您不會將SSL用於管理員。 這是預設值。 | 否 |
| `--admin-use-security-key` | 1會使應用程式使用隨機產生的索引鍵值來存取管理員和表單中的頁面。 這些索引鍵值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br><br>`0` 停用金鑰的使用。 | 否 |
| `--session-save` | 使用下列任一項：<br><br>- `db` 將會話資料儲存在資料庫中。 如果您有群集資料庫，請選擇資料庫儲存；否則，與基於檔案的儲存相比，可能沒有多少好處。<br><br>- `files` 將會話資料儲存在檔案系統中。 除非檔案系統訪問速度慢、您有群集資料庫，或您要將會話資料儲存在Redis中，否則基於檔案的會話儲存是適當的。<br><br>- `redis` 將會話資料儲存在Redis中。 如果您使用Redis進行預設或頁面快取，則必須已安裝Redis。 有關配置對Redis的支援的其他資訊，請參閱使用Redis以儲存會話。 | 否 |
| `--key` | 如果您有密鑰，請指定用於加密資料庫中的敏感資料的密鑰。 如果您沒有，應用程式會為您產生一個。 | 是 |
| `--cleanup-database` | 要在安裝Adobe Commerce或Magento Open Source之前刪除資料庫表，請指定此參數，但不帶值。 否則，資料庫將保持不變。 | 否 |
| `--db-init-statements` | 高級MySQL配置參數。 使用資料庫初始化語句在連接到MySQL資料庫時運行。 設定任何值之前，請先參考類似於此的參考。<br><br>預設為 `SET NAMES utf8;`. | 否 |
| `--sales-order-increment-prefix` | 指定要用作銷售訂單前置詞的字串值。 這通常用於保證支付處理者的唯一訂單編號。 | 否 |

**搜尋引擎設定選項：**

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--search-engine` | 要用作搜尋引擎的Elasticsearch或OpenSearch版本。 可能的值包括 `elasticsearch7`, `elasticsearch6`，和 `elasticsearch5`. 預設為 `elasticsearch7`. 要使用OpenSearch，請指定 `elasticsearch7`. Elasticsearch5已淘汰，不建議使用。 | 否 |
| `--elasticsearch-host` | 執行搜尋引擎的主機名稱或IP位址。 預設為 `localhost`. | 否 |
| `--elasticsearch-port` | 傳入HTTP請求的埠。 預設為 `9200`. | 否 |
| `--elasticsearch-index-prefix` | 識別搜尋引擎索引的前置詞。 預設為 `magento2`. | 否 |
| `--elasticsearch-timeout` | 系統超時前的秒數。 預設為 `15`. | 否 |
| `--elasticsearch-enable-auth` | 在搜尋引擎伺服器上啟用驗證。 預設為 `false`. | 否 |
| `--elasticsearch-username` | 驗證搜尋引擎的使用者ID | 否，除非已啟用驗證 |
| `--elasticsearch-password` | 驗證搜尋引擎的密碼 | 否，除非已啟用驗證 |

**RabbitMQ配置選項：**

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--amqp-host` | 請勿使用 `--amqp` 選項，除非您已設定RabbitMQ安裝。 有關安裝和配置RabbitMQ的詳細資訊，請參閱RabbitMQ安裝。<br><br>安裝RabbitMQ的主機名。 | 否 |
| `--amqp-port` | 用於連接到RabbitMQ的埠。 預設為5672。 | 否 |
| `--amqp-user` | 連接到RabbitMQ的用戶名。 請勿使用預設使用者 `guest`. | 否 |
| `--amqp-password` | 連接到RabbitMQ的密碼。 請勿使用預設密碼 `guest`. | 否 |
| `--amqp-virtualhost` | 用於連接到RabbitMQ的虛擬主機。 預設為 `/`. | 否 |
| `--amqp-ssl` | 指示是否連接到RabbitMQ。 預設為 `false`. 有關為RabbitMQ設定SSL的資訊，請參閱RabbitMQ。 | 否 |
| `--consumers-wait-for-messages` | 消費者是否應等待來自佇列的訊息？ 1 — 是，0 — 否 | 否 |

**鎖定配置選項：**

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供程式名稱。<br><br>可用的鎖定提供程式： `db`, `zookeeper`, `file`.<br><br>預設鎖定提供程式： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫前置詞 `db` 鎖定提供程式。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用時連接到Zookeeper群集的主機和埠 `zookeeper` 鎖定提供程式。<br><br>例如： `127.0.0.1:2181` | 是，若您設定 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存鎖的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 保存檔案鎖的路徑。 | 是，若您設定 `--lock-provider=file` |

**消費者配置選項：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>若要在安裝Adobe Commerce或Magento Open Source後啟用或停用模組，請參閱 [啟用和停用模組](tutorials/manage-modules.md).

**敏感資料：**

{{$include /help/_includes/sensitive-data.md}}

### 本地主機安裝示例

下列範例顯示在本機安裝Adobe Commerce的命令，並提供各種選項。

#### 範例1 — 使用管理員使用者帳戶進行基本安裝

下列範例會安裝具有下列選項的Adobe Commerce或Magento Open Source:

* 應用程式安裝在 `magento2` 與Web伺服器上的docroot相關的目錄 `localhost` 而管理員的路徑是 `admin`;因此：

   您的店面URL為 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於同一主機上。

   資料庫名稱為 `magento`，且使用者名稱和密碼均為 `magento`

* 使用伺服器重新寫入

* 管理員具有以下屬性：

   * 名字和姓氏是 `Magento User`
   * 用戶名為 `admin` 密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美國英語）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* OpenSearch 1.2安裝在 `es-host.example.com` 並在埠9200上連接

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

顯示的訊息類似於以下，表示安裝成功：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 範例2 — 不使用管理員使用者帳戶進行基本安裝

您可以安裝Adobe Commerce或Magento Open Source，而不需建立管理員使用者，如下列範例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

如果安裝成功，則會顯示下列訊息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安裝後，您可以使用 `admin:user:create` 命令：
[建立或編輯管理員](tutorials/admin.md#create-or-edit-an-administrator)

#### 範例3 — 使用其他選項安裝

下列範例會安裝具有下列選項的Adobe Commerce或Magento Open Source:

* 應用程式安裝在 `magento2` 與Web伺服器上的docroot相關的目錄 `localhost` 而管理員的路徑是 `admin`;因此：

   您的店面URL為 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於同一主機上。

   資料庫名稱為 `magento`，且使用者名稱和密碼均為 `magento`

* 管理員具有以下屬性：

   * 名字和姓氏是 `Magento User`
   * 用戶名為 `admin` 密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美國英語）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* 安裝程式首先清除資料庫，然後安裝表和模式
* 您可以使用銷售訂單增量首碼 `ORD$` (因為它包含特殊字元 [`$`]，值必須以雙引號括住)
* 會話資料保存在資料庫中
* 使用伺服器重新寫入
* Elasticsearch7安裝在 `es-host.example.com` 並在埠9200上連接

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>您必須在單行上輸入命令，或如上例所示，使用 `\` 字元。

如果安裝成功，則會顯示下列訊息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
