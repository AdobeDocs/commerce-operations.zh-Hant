---
title: 建立或更新部署配置
description: 請依照下列步驟管理您的Adobe Commerce或Magento Open Source部署設定。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# 建立或更新部署配置

使用此命令沒有先決條件。

## 建立或更新部署配置

[部署配置](../../configuration/reference/deployment-files.md) 提供應用程式初始化和引導所需的資訊。

在以下情況下，可以使用此命令：

* 您先前已安裝應用程式，並且要修改部署配置
* 您只想建立部署配置，然後以其他方式繼續安裝
* 更新部署配置而不影響其他任何操作

命令選項：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

下表討論了安裝參數和值的含義。

| 參數 | 值 | 必要？ |
|--- |--- |--- |
| `--backend-frontname` | 統一資源標識符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))以存取管理員。<br><br>為防止木馬程式遭到攻擊，建議您不要使用管理、後端等常見字詞。 管理URI可包含英數字元值和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一項：<br><br> — 資料庫伺服器的完全限定主機名或IP地址。<br><br>- `localhost` （預設）或 `127.0.0.1` 如果資料庫伺服器與Web伺服器位於同一主機上。 localhost表示MySQL客戶端庫使用UNIX套接字連接到資料庫。 `127.0.0.1` 導致客戶端庫使用TCP協定。 有關套接字的詳細資訊，請參見 [PHP PDO_MYSQL文檔](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 可以選擇在其主機名中指定資料庫伺服器埠，如 `www.example.com:9000` | 否 |
| `--db-name` | 要安裝資料庫表的資料庫實例的名稱。<br><br>預設為 `magento2`. | 否 |
| `--db-user` | 資料庫實例所有者的用戶名。<br><br>預設為 `root`. | 否 |
| `--db-password` | 資料庫實例所有者的密碼。 | 否 |
| `--db-prefix` | 僅當在資料庫實例中安裝資料庫表時才使用，該實例中已有Adobe Commerce表和Magento Open Source表。<br><br>在這種情況下，請使用前置詞來標識此安裝的表。 有些客戶在伺服器上執行多個Adobe Commerce或Magento Open Source執行個體，且同一資料庫中的所有表格皆在其中。<br><br>前置詞長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和底線字元。<br><br>此選項允許這些客戶與多個Adobe Commerce或Magento Open Source安裝共用資料庫伺服器。 | 否 |
| `--session-save` | 使用下列任一項：<br><br>- `db` 若要將工作階段資料儲存在 [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). 如果您有群集資料庫，請選擇資料庫儲存；否則，與基於檔案的儲存相比，可能沒有多少好處。<br><br>- `files` 將會話資料儲存在檔案系統中。 除非檔案系統訪問速度慢、您有群集資料庫，或您要將會話資料儲存在Redis中，否則基於檔案的會話儲存是適當的。<br><br>- `redis` 若要儲存工作階段資料 [使用Redi作為會話儲存](../../configuration/cache/config-redis.md). 如果您使用Redis進行預設或頁面快取，則必須已安裝Redis。 | 否 |
| `--key` | 如果您有，請指定要加密的金鑰 [敏感資料](#sensitive-data) 在資料庫中。 如果您沒有，應用程式會為您產生一個。 | 否 |
| `--db-init-statements` | 高級MySQL配置參數。 使用資料庫初始化語句在連接到MySQL資料庫時運行。<br><br>預設為 `SET NAMES utf8;`.<br><br>請參閱類似以下的參考資料 [這個](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 設定任何值之前。 | 否 |
| `--http-cache-hosts` | 要向其發送清除請求的HTTP快取網關主機的逗號分隔清單。 （例如，清漆伺服器。） 使用此參數可指定要在相同請求中清除的主機或主機。 （您只有一台主機或多台主機並不重要。）<br><br>格式必須為 `<hostname or ip>:<listen port>`，此時您可以忽略 `<listen port>` 如果是80號港。 例如， `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. 請勿以空格字元分隔主機。 | 否 |

## 匯入設定資料

設定生產系統時，最好從匯入組態設定 `config.php` 和 `env.php` 進入資料庫。
這些設定包括配置路徑和值、網站、儲存、儲存檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以建立產品屬性，並套用至生產系統上的網站、商店和商店檢視。

在生產系統上，執行下列命令以從組態檔匯入資料(`config.php` 和 `env.php`)到資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

選填 `[-n, --no-interaction]` 標幟允許命令在不進行其他確認的情況下運行。

欲知其他資訊，請查看 [從組態檔匯入資料](../../configuration/cli/import-configuration.md)

### 敏感資料

{{$include /help/_includes/sensitive-data.md}}
