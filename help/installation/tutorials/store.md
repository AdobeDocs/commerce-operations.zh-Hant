---
title: 設定存放區
description: 請依照下列步驟設定您的Adobe Commerce存放區。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 設定存放區

在執行這個命令之前，您必須執行下列動作&#x200B;*或*，您必須[安裝應用程式](../advanced.md)：

* [建立或更新部署設定](deployment.md)
* [建立資料庫綱要](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 設定存放區

命令使用方式：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

下表定義引數和值：

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--base-url` | 以下列任何格式存取管理員和店面的基底URL： <br><br>- `http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：**&#x200B;配置（`http://`或`https://`）和結尾斜線都是必要的。 `<your install dir>`是安裝應用程式的docroot相對路徑。 根據您設定網頁伺服器和虛擬主機的方式，路徑可能是magento2或可能為空白。<br><br>若要存取localhost上的應用程式，您可以使用`http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}`，代表虛擬主機設定或Docker等虛擬化環境所定義的基底URL。 例如，若您以主機名稱commerce.example.com設定虛擬主機，則可以以`--base-url={{base_url}}`安裝應用程式，並以`http://commerce.example.com/admin`之類的URL存取管理員。 | 否 |
| `--language` | 在管理員和店面中使用的語言代碼。<br><br>（如果您尚未這樣做，可以從`bin`目錄輸入`magento info:language:list`來檢視語言代碼清單。） | 否 |
| `--currency` | 店面中使用的預設貨幣。 <br><br>（如果您尚未這樣做，可以從`bin`目錄輸入`magento info:currency:list`來檢視貨幣清單。） | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 （如果您尚未這樣做，您可以從`bin`目錄輸入`magento info:timezone:list`來檢視時區清單。） | 否 |
| `--use-rewrites` | `1`表示您對店面和管理程式中產生的連結使用網頁伺服器重寫。<br><br>`0`停用網頁伺服器重寫的使用。 這是預設值。 | 否 |
| `--use-secure` | `1`允許在店面URL中使用安全通訊端層(SSL)。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`停用使用SSL。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 安全基底URL，用於以下列格式存取您的管理員和店面： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1`表示您使用SSL來存取管理員。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0`表示您沒有使用SSL與管理員。 這是預設值。 | 否 |
| `--admin-use-security-key` | `1`導致應用程式使用隨機產生的金鑰值來存取管理員和表單中的頁面。 這些金鑰值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br/><br/>`0`停用金鑰。 | 否 |
| `--magento-init-params` | 新增至任何命令以自訂應用程式初始化引數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |
