---
title: 建立或更新部署設定
description: 請依照下列步驟管理您的Adobe Commerce部署設定。
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# 建立或更新部署設定

使用此命令沒有先決條件。

## 建立或更新部署設定

[部署組態](../../configuration/reference/deployment-files.md)提供應用程式初始化及啟動所需的資訊。

在下列情況下，可以使用此命令：

* 您先前已安裝應用程式，且想要修改部署設定
* 您只想建立部署組態，並以其他方式繼續安裝
* 更新部署設定而不影響其他任何專案

命令選項：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

下表討論安裝引數和值的意義。

| 引數 | 值 | 必填？ |
|--- |--- |--- |
| `--backend-frontname` | 用於存取管理員的統一資源識別碼([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。<br><br>為防止利用漏洞，建議您不要使用常見的字詞，例如admin、backend。 管理員URI只能包含英數字元和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一項：<br><br> — 資料庫伺服器的完整主機名稱或IP位址。<br><br>- `localhost` （預設）或`127.0.0.1` （如果您的資料庫伺服器與Web伺服器位於相同的主機上）。 localhost表示MySQL使用者端程式庫使用UNIX通訊端連線到資料庫。 `127.0.0.1`導致使用者端資料庫使用TCP通訊協定。 如需通訊端的詳細資訊，請參閱[PHP PDO_MYSQL檔案](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注意：**&#x200B;您可以選擇在其主機名稱中指定資料庫伺服器連線埠，例如`www.example.com:9000` | 否 |
| `--db-name` | 您要安裝資料庫表格的資料庫執行處理名稱。<br><br>預設為`magento2`。 | 否 |
| `--db-user` | 資料庫執行處理擁有者的使用者名稱。<br><br>預設為`root`。 | 否 |
| `--db-password` | 資料庫執行處理擁有者的密碼。 | 否 |
| `--db-prefix` | 只有在您要在已經有Adobe Commerce表格的資料庫執行個體中安裝資料庫表格時才使用。<br><br>在這種情況下，請使用前置字元來識別此安裝的資料表。 有些客戶在含有相同資料庫中所有表格的伺服器上執行多個Adobe Commerce執行個體。<br><br>首碼的長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和下劃線字元。<br><br>此選項可讓這些客戶共用一個以上Adobe Commerce安裝的資料庫伺服器。 | 否 |
| `--session-save` | 使用下列任一項： <br><br>- `db`將工作階段資料儲存在[資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)。 如果您有叢集資料庫，請選擇資料庫儲存體；否則，與檔案式儲存體相比，可能不會有多大好處。<br><br>- `files`將工作階段資料儲存在檔案系統中。 除非檔案系統存取緩慢、您有叢集資料庫，或您想要將工作階段資料儲存在Redis中，否則檔案式工作階段儲存體是適當的。<br><br>- `redis`將工作階段資料儲存在[使用Redis作為工作階段存放區](../../configuration/cache/config-redis.md)。 如果您使用Redis作為預設或頁面快取，則必須已安裝Redis。 | 否 |
| `--key` | 如果您有密碼，請指定金鑰以加密資料庫中的[機密資料](#sensitive-data)。 如果您沒有，應用程式會為您產生一個。 | 否 |
| `--db-init-statements` | 進階MySQL設定引數。 在連線到MySQL資料庫時，使用資料庫初始化陳述式來執行。<br><br>預設為`SET NAMES utf8;`。<br><br>設定任何值之前，請先查閱類似[這個](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)的參考。 | 否 |
| `--http-cache-hosts` | 要傳送清除請求的HTTP快取閘道主機清單（以逗號分隔）。 （例如Varnish伺服器）。 您可以使用此引數，指定要在相同要求中永久刪除的一或多個主機。 （您只有一個主機或多個主機並不重要。）<br><br>格式必須是`<hostname or ip>:<listen port>`，若是連線埠80，則可以省略`<listen port>`。 例如，`--http-cache-hosts=192.0.2.100,192.0.2.155:6081`。 請勿以空格字元分隔主機。 | 否 |

## 匯入設定資料

設定生產系統時，最好將組態設定從`config.php`和`env.php`匯入資料庫。
這些設定包括配置路徑和值、網站、商店、商店檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以在生產系統上建立產品屬性，並將其套用至網站、商店和商店檢視。

在生產系統上，執行下列命令以從組態檔（`config.php`和`env.php`）匯入資料到資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

選用的`[-n, --no-interaction]`旗標可讓命令在不進行其他確認的情況下執行。

如需其他資訊，請檢查[從組態檔匯入資料](../../configuration/cli/import-configuration.md)

### 敏感資料

{{$include /help/_includes/sensitive-data.md}}

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
