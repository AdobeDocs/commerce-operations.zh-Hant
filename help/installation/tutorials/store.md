---
title: 設定商店
description: 請依照下列步驟設定您的Adobe Commerce或Magento Open Source存放區。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# 設定商店

在運行此命令之前，您必須執行以下操作 *或* 您必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 設定商店

命令用法：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

其中下表定義參數和值：

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--base-url` | 以下列任何格式用來存取管理員和店面的基本URL:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 計畫(`http://` 或 `https://`)和尾隨斜線皆為必要。 `<your install dir>` 是安裝應用程式的相對路徑。 視您設定Web伺服器和虛擬主機的方式而定，路徑可能是magento2，也可能是空白的。<br><br>要在localhost上訪問應用程式，可以使用 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 它表示由虛擬主機設定或虛擬化環境（如Docker）定義的基本URL。 例如，如果您使用hostname commerce.example.com設定虛擬主機，則可以使用安裝應用程式 `--base-url={{base_url}}` 並使用URL(如 `http://commerce.example.com/admin`. | 否 |
| `--language` | 要在管理員和店面中使用的語言代碼。<br><br>(如果您尚未這麼做，您可以輸入 `magento info:language:list` 從 `bin` 目錄。) | 否 |
| `--currency` | 要在店面中使用的預設貨幣。 <br><br>(如果您尚未這麼做，您可以輸入 `magento info:currency:list` 從 `bin` 目錄。) | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 (如果您尚未這麼做，您可以輸入 `magento info:timezone:list` 從 `bin` 目錄。) | 否 |
| `--use-rewrites` | `1` 表示您在storefront和「管理員」中，對產生的連結使用web伺服器重寫。<br><br>`0` 禁用web伺服器重寫的使用。 這是預設值。 | 否 |
| `--use-secure` | `1` 允許在店面URL中使用安全套接字層(SSL)。 選取此選項之前，請確定您的Web伺服器支援SSL。<br><br>`0` 停用SSL的使用。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 以下列格式用來存取管理員和店面的安全基本URL: `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL存取管理員。 選取此選項之前，請確定您的Web伺服器支援SSL。<br><br>`0` 表示您不會將SSL用於管理員。 這是預設值。 | 否 |
| `--admin-use-security-key` | `1` 會使應用程式使用隨機產生的索引鍵值來存取管理員和表單中的頁面。 這些索引鍵值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br/><br/>`0` 停用金鑰的使用。 | 否 |
| `--magento-init-params` | 添加到任何命令以自定義應用程式初始化參數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |
