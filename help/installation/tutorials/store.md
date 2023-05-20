---
title: 配置儲存
description: 按照以下步驟配置您的Adobe Commerce或Magento Open Source商店。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 配置儲存

在運行此命令之前，必須執行以下操作 *或* 必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 配置儲存

命令用法：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

其中，下表定義了參數和值：

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--base-url` | 用於以下列任何格式訪問管理員和店面的基本URL:<br><br>- `http[s]://<host or ip>/<your install dir>/`。<br><br>**注：** 計畫(`http://` 或 `https://`)和尾斜槓都是必需的。 `<your install dir>` 是安裝應用程式的相對路徑。 根據您如何設定Web伺服器和虛擬主機，路徑可能為magento2或為空。<br><br>要訪問localhost上的應用程式，可以使用 `http://127.0.0.1/<your install dir>/`。<br><br>- `{{base_url}}` 它表示由虛擬主機設定或Docker等虛擬化環境定義的基URL。 例如，如果您使用hostname commerce.example.com設定虛擬主機，則可以使用 `--base-url={{base_url}}` 並使用URL訪問Admin `http://commerce.example.com/admin`。 | 否 |
| `--language` | 要在管理和店面中使用的語言代碼。<br><br>(如果尚未這樣做，可通過輸入 `magento info:language:list` 從 `bin` )。 | 否 |
| `--currency` | 要在店面中使用的預設貨幣。 <br><br>(如果尚未這樣做，可通過輸入 `magento info:currency:list` 從 `bin` )。 | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 (如果尚未這樣做，可通過輸入 `magento info:timezone:list` 從 `bin` )。 | 否 |
| `--use-rewrites` | `1` 表示在storefront和Admin中對生成的連結使用web伺服器重寫。<br><br>`0` 禁用Web伺服器重寫。 這是預設值。 | 否 |
| `--use-secure` | `1` 啟用在店面URL中使用安全套接字層(SSL)。 在選擇此選項之前，請確保Web伺服器支援SSL。<br><br>`0` 禁用SSL。 在這種情況下，所有其它安全URL選項都假定為0。 這是預設值。 | 否 |
| `--base-url-secure` | 安全基URL，用於以下格式訪問管理員和商店： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL訪問Admin。 在選擇此選項之前，請確保Web伺服器支援SSL。<br><br>`0` 表示您不與Admin一起使用SSL。 這是預設值。 | 否 |
| `--admin-use-security-key` | `1` 導致應用程式使用隨機生成的鍵值訪問管理和表單中的頁面。 這些鍵值有助於防止跨站點指令碼偽造攻擊。 這是預設值。<br/><br/>`0` 禁用鍵的使用。 | 否 |
| `--magento-init-params` | 添加到任何命令以自定義應用程式初始化參數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |
