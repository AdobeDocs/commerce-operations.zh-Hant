---
title: 安裝Adobe Commerce
description: 按照以下步驟在您擁有的基礎架構上安裝Adobe Commerce或Magento Open Source。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2106'
ht-degree: 0%

---

# 安裝Adobe Commerce

開始之前，請完成以下步驟：

* 驗證您的系統是否滿足中討論的要求 [系統要求](../system-requirements.md)。

* 全部完成 [先決條件](../prerequisites/overview.md) 的子菜單。

* 完成第一個安裝步驟。 請參閱 [您的安裝或升級路徑](../overview.md)。

* 登錄到應用程式伺服器後， [切換到檔案系統所有者](../prerequisites/file-system/overview.md)。

* 查看 [開始安裝命令行](../composer.md) 概述。

>[!NOTE]
>
>必須從應用程式 `bin` 子目錄。

可以使用不同選項多次運行安裝程式以完成以下安裝任務：

* 分階段安裝 — 例如，在為安全套接字層(SSL)配置Web伺服器後，可以再次運行安裝程式以設定SSL選項。

* 更正以前安裝中的錯誤。

* 將應用程式安裝到其他資料庫實例中。

>[!NOTE]
>
>預設情況下，如果在同一資料庫實例中安裝了Commerce軟體，安裝程式不會覆蓋資料庫。 可以使用 `cleanup-database` 參數以更改此行為。

另請參閱 [更新、重新安裝、卸載](uninstall.md)。

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 安裝程式幫助命令

您可以運行以下命令來查找某些必需參數的值：

| 安裝程式參數 | 命令 |
| ------------------ | ------------------------------- |
| 語言 | `magento info:language:list` |
| 貨幣 | `magento info:currency:list` |
| 時區 | `magento info:timezone:list` |

>[!NOTE]
>
>如果在運行這些命令時顯示錯誤，請驗證是否更新了安裝依賴項，如中所述 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)。

## 從命令行安裝

install命令使用以下格式：

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

下表描述了安裝選項的名稱和值，如安裝命令。 請參閱 [本地主機安裝示例](#sample-localhost-installations)。

>[!NOTE]
>
>任何包含空格或特殊字元的選項都必須用單引號或雙引號括起來。

**管理員憑據：**

以下選項指定管理員用戶的用戶資訊和憑據。

在Adobe Commerce版本2.2.8和更高版本中，您可以在安裝期間或安裝後建立管理員用戶。 如果在安裝過程中建立用戶，則需要所有管理員憑據變數。 請參閱 [本地主機安裝示例](#sample-localhost-installations)。

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員用戶的名。 | 是 |
| `--admin-lastname` | 管理員用戶的姓。 | 是 |
| `--admin-email` | 管理員用戶的電子郵件地址。 | 是 |
| `--admin-user` | 管理員用戶名。 | 是 |
| `--admin-password` | 管理員用戶密碼。 密碼的長度必須至少為7個字元，並且必須至少包含一個字母和至少一個數字字元。 我們建議使用更長、更複雜的密碼。 用單引號將整個密碼字串括起來。 比如說， `--admin-password='A0b9%t3g'` | 是 |

**站點和資料庫配置選項：**

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--base-url` | 用於以下列任何格式訪問管理員和店面的基本URL:<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注：** 方案(http://或https://)和尾斜槓都是必需的。<br><br>`<your install dir>` 是安裝應用程式的相對路徑。 根據您如何設定Web伺服器和虛擬主機，路徑可能為magento2或為空。<br><br>要訪問localhost上的應用程式，可以使用 `http://127.0.0.1/<your install dir>/` 或 `http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}` 它表示由虛擬主機設定或Docker等虛擬化環境定義的基URL。 例如，如果您使用hostname commerce.example.com設定虛擬主機，則可以使用 `--base-url={{base_url}}` 並使用URL訪問Admin `http://commerce.example.com/admin`。 | 是 |
| `--backend-frontname` | 統一資源標識符(URI)，用於訪問管理員。 可以省略此參數，以便應用程式使用以下模式admin_jkhgdfq為您生成隨機URI</code>。<br><br>為安全起見，我們建議隨機URI。 隨機URI對駭客或惡意軟體來說更難利用。<br><br>URI顯示在安裝結束時。 您可以隨時使用 `magento info:adminuri` 的子菜單。<br><br>如果您選擇輸入值，建議您不要使用諸如admin 、 backend之類的通用詞。 管理員URI可以包含字母數字值和下划線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一選項：<br><br> — 資料庫伺服器的完全限定主機名或IP地址。<br><br>- `localhost` （預設）或 `127.0.0.1` 如果資料庫伺服器與web server.localhost位於同一主機上，則表示MySQL客戶端庫使用UNIX套接字連接到資料庫。 `127.0.0.1` 使客戶端庫使用TCP協定。 有關套接字的詳細資訊，請參見 [PHP PDO_MYSQL文檔](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注：** 您可以選擇在其主機名中指定資料庫伺服器埠，如www.example.com:9000 | 是 |
| `--db-name` | 要在其中安裝資料庫表的資料庫實例的名稱。<br><br>預設值為 `magento2`。 | 是 |
| `--db-user` | 資料庫實例所有者的用戶名。<br><br>預設值為 `root`。 | 是 |
| `--db-password` | 資料庫實例所有者的密碼。 | 是 |
| `--db-prefix` | 僅當在已包含Adobe Commerce表或Magento Open Source表的資料庫實例中安裝資料庫表時才使用。<br><br>在這種情況下，請使用前置詞來標識此安裝的表。 有些客戶在伺服器上運行多個Adobe Commerce和Magento Open Source實例，並且所有表都位於同一資料庫中。<br><br>前置詞長度最多可以為五個字元。 它必須以字母開頭，並且只能包含字母、數字和下划線字元。<br><br>此選項允許這些客戶共用資料庫伺服器並安裝多個安裝。 | 否 |
| `--db-ssl-key` | 客戶端密鑰的路徑。 | 否 |
| `--db-ssl-cert` | 客戶端證書的路徑。 | 否 |
| `--db-ssl-ca` | 伺服器證書的路徑。 | 否 |
| `--language` | 要在管理和店面中使用的語言代碼。 (如果尚未這樣做，可通過輸入 `magento info:language:list` 的子目錄。) | 否 |
| `--currency` | 要在店面中使用的預設貨幣。 (如果尚未這樣做，可通過輸入 `magento info:currency:list` 的子目錄。) | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 (如果尚未這樣做，可通過輸入 `magento info:timezone:list` 的子目錄。) | 否 |
| `--use-rewrites` | `1` 表示在storefront和Admin中對生成的連結使用web伺服器重寫。<br><br>`0` 禁用Web伺服器重寫。 這是預設值。 | 否 |
| `--use-secure` | `1` 啟用在店面URL中使用安全套接字層(SSL)。 在選擇此選項之前，請確保Web伺服器支援SSL。<br><br>`0` 禁用SSL。 在這種情況下，所有其它安全URL選項都假定為0。 這是預設值。 | 否 |
| `--base-url-secure` | 安全基URL，用於以下格式訪問管理員和商店： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL訪問Admin。 在選擇此選項之前，請確保Web伺服器支援SSL。<br><br>`0` 表示您不與Admin一起使用SSL。 這是預設值。 | 否 |
| `--admin-use-security-key` | 1導致應用程式使用隨機生成的鍵值訪問管理和表單中的頁面。 這些鍵值有助於防止跨站點指令碼偽造攻擊。 這是預設值。<br><br>`0` 禁用鍵的使用。 | 否 |
| `--session-save` | 使用下列任一選項：<br><br>- `db` 將會話資料儲存到資料庫中。 如果有群集資料庫，請選擇資料庫儲存；否則，與基於檔案的儲存相比，可能沒有什麼好處。<br><br>- `files` 將會話資料儲存在檔案系統中。 基於檔案的會話儲存是適當的，除非檔案系統訪問速度慢、您有群集資料庫或您想在Redis中儲存會話資料。<br><br>- `redis` 將會話資料儲存在Redis中。 如果使用Redis進行預設或頁面快取，則必須已安裝Redis。 有關配置對Redis的支援的其他資訊，請參見Use Redis for session storage。 | 否 |
| `--key` | 如果您有密鑰，請指定一個密鑰以加密資料庫中的敏感資料。 如果您沒有，應用程式將為您生成一個。 | 是 |
| `--cleanup-database` | 要在安裝應用程式之前刪除資料庫表，請指定此參數，但不帶值。 否則，資料庫將保持不變。 | 否 |
| `--db-init-statements` | 高級MySQL配置參數。 使用資料庫初始化語句在連接到MySQL資料庫時運行。 在設定任何值之前，請參考與此引用類似的引用。<br><br>預設值為 `SET NAMES utf8;`。 | 否 |
| `--sales-order-increment-prefix` | 指定用作銷售訂單前置詞的字串值。 通常，這用於保證支付處理者的唯一訂單編號。 | 否 |

>[!TIP]
>
>要在安裝期間啟用遠程儲存服務，請參見 [配置遠程儲存](../../configuration/remote-storage/remote-storage.md) 的 _配置指南_。

**搜索引擎配置選項：**

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--search-engine` | 搜索引擎的版本。 可能的值為 `elasticsearch7`。 `elasticsearch6`, `elasticsearch5`。 預設值為 `elasticsearch7`。 如果已將OpenSearch安裝為搜索引擎，請指定值 `elasticsearch7`。 Elasticsearch5已棄用，不建議使用。 | 否 |
| `--elasticsearch-host` | 運行搜索引擎的主機名或IP地址。 預設值為 `localhost`。 | 否 |
| `--elasticsearch-port` | 傳入HTTP請求的埠。 預設值為 `9200`。 | 否 |
| `--elasticsearch-index-prefix` | 標識搜索索引的前置詞。 預設值為 `magento2`。 | 否 |
| `--elasticsearch-timeout` | 系統超時前的秒數。 預設值為 `15`。 | 否 |
| `--elasticsearch-enable-auth` | 在搜索引擎伺服器上啟用身份驗證。 預設值為 `false`。 | 否 |
| `--elasticsearch-username` | 要驗證的用戶ID | 否，除非啟用身份驗證 |
| `--elasticsearch-password` | 要驗證的密碼 | 否，除非啟用身份驗證 |

**[!DNL RabbitMQ]配置選項：**

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--amqp-host` | 不要使用 `--amqp` 選項，除非您已設定 [!DNL RabbitMQ]。 請參閱 [!DNL RabbitMQ] 安裝，以瞭解有關安裝和配置的詳細資訊 [!DNL RabbitMQ]。<br><br>主機名，其中 [!DNL RabbitMQ] 已安裝。 | 否 |
| `--amqp-port` | 用於連接到的埠 [!DNL RabbitMQ]。 預設為5672。 | 否 |
| `--amqp-user` | 用於連接到的用戶名 [!DNL RabbitMQ]。 不使用預設用戶 `guest`。 | 否 |
| `--amqp-password` | 用於連接到的密碼 [!DNL RabbitMQ]。 不使用預設密碼 `guest`。 | 否 |
| `--amqp-virtualhost` | 用於連接到的虛擬主機 [!DNL RabbitMQ]。 預設值為 `/`。 | 否 |
| `--amqp-ssl` | 指示是否連接到 [!DNL RabbitMQ]。 預設值為 `false`。 請參閱 [!DNL RabbitMQ] 有關為 [!DNL RabbitMQ]。 | 否 |
| `--consumers-wait-for-messages` | 消費者是否應等待隊列中的消息？ 1 — 是，0 — 否 | 否 |

**遠程儲存選項：**

| 名稱 | 說明 | 需要？ |
|--- |--- |--- |
| `remote-storage-driver` | 適配器名稱<br>可能的值：<br>**檔案**:禁用遠程儲存並使用本地檔案系統&#x200B;<br>**aws-s3**:使用 [Amazon簡單儲存服務(AmazonS3)](https://aws.amazon.com/s3/) | 否 |
| `remote-storage-bucket` | 對象儲存或容器名稱 | 否 |
| `remote-storage-prefix` | 可選前置詞（對象儲存內部的位置） | 否 |
| `remote-storage-region` | 區域名稱 | 否 |
| `remote-storage-key` | 可選訪問密鑰 | 否 |
| `remote-storage-secret` | 可選密鑰 | 否 |

**鎖定配置選項：**

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供程式名稱。<br><br>可用鎖提供程式： `db`。 `zookeeper`。 `file`。<br><br>預設鎖提供程式： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫前置詞 `db` 鎖定提供程式。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用時連接到Zookeeper群集的主機和埠 `zookeeper` 鎖定提供程式。<br><br>例如： `127.0.0.1:2181` | 是的，如果 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存鎖的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 保存檔案鎖的路徑。 | 是的，如果 `--lock-provider=file` |

**使用者配置選項：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>要在安裝應用程式後啟用或禁用模組，請參見 [啟用和禁用模組](manage-modules.md)。

**敏感資料：**

{{$include /help/_includes/sensitive-data.md}}

### 本地主機安裝示例

以下示例顯示了使用各種選項在本地安裝Adobe Commerce的命令。

#### 示例1 — 使用管理員用戶帳戶進行基本安裝

以下示例使用以下選項安裝應用程式：

* 應用程式安裝在 `magento2` 與Web伺服器docroot相關的目錄 `localhost` 而管理員的路徑是 `admin`;因此：

   你的店面URL是 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於同一主機上。

   資料庫名稱為 `magento`，並且用戶名和密碼 `magento`

* 使用伺服器重寫

* 管理員具有以下屬性：

   * 名字和姓是 `Commerce User`
   * 用戶名為 `admin` 密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美國英語）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* Elasticsearch7安裝在 `es-host.example.com` 並連接到埠9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

與以下顯示類似的消息，指示安裝成功：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 示例2 — 基本安裝，不使用管理員用戶帳戶

您無需建立管理員用戶即可安裝應用程式，如下例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

如果安裝成功，將顯示以下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安裝後，可以使用 `admin:user:create` 命令：
[建立或編輯管理員](admin.md#create-or-edit-an-administrator)

#### 示例3 — 安裝時附加選項

以下示例使用以下選項安裝應用程式：

* Magapplication安裝在 `magento2` 與Web伺服器docroot相關的目錄 `localhost` 而管理員的路徑是 `admin`;因此：

   你的店面URL是 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於同一主機上。

   資料庫名稱為 `magento`，並且用戶名和密碼 `magento`

* 管理員具有以下屬性：

   * 名字和姓是 `Commerce User`
   * 用戶名為 `admin` 密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美國英語）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* 安裝程式在安裝表和架構之前首先清除資料庫
* 使用 `ORD$` 銷售訂單增量前置詞(因為它包含特殊字元 [`$`]，值必須用雙引號括起來)
* 會話資料保存在資料庫中
* 使用伺服器重寫
* Elasticsearch7安裝在 `es-host.example.com` 並連接到埠9200

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
>必須在單行上輸入命令，或如上例所示， `\` 字元。

如果安裝成功，將顯示以下消息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>如果您有一個用戶帳戶可以訪問應用程式伺服器，請參閱 [設定umask](../next-steps/set-umask.md)。 此類型的設定是共用主機的典型設定。
