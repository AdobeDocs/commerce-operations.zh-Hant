---
title: 建立或更新部署配置
description: 按照以下步驟管理您的Adobe Commerce或Magento Open Source部署配置。
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# 建立或更新部署配置

使用此命令沒有先決條件。

## 建立或更新部署配置

[部署配置](../../configuration/reference/deployment-files.md) 提供了應用程式初始化和引導所需的資訊。

如果：

* 您以前安裝了應用程式，並且要修改部署配置
* 您只想建立部署配置，並以其他方式繼續安裝
* 更新部署配置而不影響任何其他內容

命令選項：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

下表討論了安裝參數和值的含義。

| 參數 | 值 | 需要？ |
|--- |--- |--- |
| `--backend-frontname` | 統一資源標識符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))以訪問Admin。<br><br>為防止利用漏洞，建議您不要使用諸如admin 、 backend之類的通用詞。 管理員URI可以包含字母數字值和下划線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一選項：<br><br> — 資料庫伺服器的完全限定主機名或IP地址。<br><br>- `localhost` （預設）或 `127.0.0.1` 資料庫伺服器與Web伺服器位於同一主機上。 localhost表示MySQL客戶端庫使用UNIX套接字連接到資料庫。 `127.0.0.1` 使客戶端庫使用TCP協定。 有關套接字的詳細資訊，請參見 [PHP PDO_MYSQL文檔](https://www.php.net/manual/en/ref.pdo-mysql.php)。<br><br>**注：** 您可以選擇在其主機名中指定資料庫伺服器埠，如 `www.example.com:9000` | 否 |
| `--db-name` | 要在其中安裝資料庫表的資料庫實例的名稱。<br><br>預設值為 `magento2`。 | 否 |
| `--db-user` | 資料庫實例所有者的用戶名。<br><br>預設值為 `root`。 | 否 |
| `--db-password` | 資料庫實例所有者的密碼。 | 否 |
| `--db-prefix` | 僅當要在已包含Adobe Commerce表和Magento Open Source表的資料庫實例中安裝資料庫表時才使用。<br><br>在這種情況下，請使用前置詞來標識此安裝的表。 有些客戶在伺服器上運行多個Adobe Commerce或Magento Open Source實例，且所有表都位於同一資料庫中。<br><br>前置詞長度最多可以為五個字元。 它必須以字母開頭，並且只能包含字母、數字和下划線字元。<br><br>此選項使這些客戶能夠共用資料庫伺服器並安裝多個Adobe Commerce或Magento Open Source。 | 否 |
| `--session-save` | 使用下列任一選項：<br><br>- `db` 將會話資料儲存在 [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)。 如果有群集資料庫，請選擇資料庫儲存；否則，與基於檔案的儲存相比，可能沒有什麼好處。<br><br>- `files` 將會話資料儲存在檔案系統中。 基於檔案的會話儲存是適當的，除非檔案系統訪問速度慢、您有群集資料庫或您想在Redis中儲存會話資料。<br><br>- `redis` 要儲存會話資料 [將Redis用於會話儲存](../../configuration/cache/config-redis.md)。 如果使用Redis進行預設或頁面快取，則必須已安裝Redis。 | 否 |
| `--key` | 如果您有密鑰，請指定要加密的密鑰 [敏感資料](#sensitive-data) 的子菜單。 如果您沒有，應用程式將為您生成一個。 | 否 |
| `--db-init-statements` | 高級MySQL配置參數。 使用資料庫初始化語句在連接到MySQL資料庫時運行。<br><br>預設值為 `SET NAMES utf8;`。<br><br>參考類似於 [這個](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 設定任何值之前。 | 否 |
| `--http-cache-hosts` | 要向其發送清除請求的HTTP快取網關主機的逗號分隔清單。 （例如，清漆伺服器。） 使用此參數可指定要在同一請求中清除的主機。 （您只有一台主機或多台主機並不重要。）<br><br>格式必須為 `<hostname or ip>:<listen port>`，在 `<listen port>` 如果是80號港。 比如說， `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`。 不要使用空格字元分隔主機。 | 否 |

## 導入配置資料

在設定生產系統時，最好從 `config.php` 和 `env.php` 資料庫中。
這些設定包括配置路徑和值、網站、儲存、儲存視圖和主題。

導入網站、商店、商店視圖和主題後，您可以建立產品屬性並將其應用於生產系統上的網站、商店和商店視圖。

在生產系統上，運行以下命令以從配置檔案導入資料(`config.php` 和 `env.php`)到資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

可選 `[-n, --no-interaction]` flag允許在不進行其他確認的情況下運行命令。

如需其他資訊，請查看 [從配置檔案導入資料](../../configuration/cli/import-configuration.md)

### 敏感資料

{{$include /help/_includes/sensitive-data.md}}
