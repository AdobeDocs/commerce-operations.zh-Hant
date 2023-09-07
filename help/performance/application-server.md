---
title: GraphQL API的應用程式伺服器
description: 請依照這些指示，在您的Adobe Commerce部署中啟用GraphQL API的應用程式伺服器。
badgeCoreBeta: label="2.4.7-beta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: 4f83a2181f6a7880b77dc07729574365def71f1d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# GraphQL API的應用程式伺服器

適用於GraphQL API的Commerce Application Server可讓Adobe Commerce維護Commerce GraphQL API請求之間的狀態，並減少每個請求的啟動載入時間。 透過在程式之間共用應用程式狀態，API要求會顯著提高效率。

此Application Server的Beta版僅供執行PHP 8.1或8.2的內部部署使用。 不支援雲端部署。 尚不支援B2B GraphQL功能。 當設定此版本的PHP應用程式伺服器時，GraphQL要求可能無法如預期般在內部部署中運作。

## 誰可以使用Application Server？

應用程式伺服器僅適用於內部部署Commerce。

## 為GraphQL API啟用應用程式伺服器

此 `ApplicationServer` 模組(`Magento/ApplicationServer/`)啟用GraphQL API的應用程式伺服器。

執行Application Server需要安裝Open Swool延伸模組，並對部署的Nginx組態檔進行微幅變更，才能在本機執行此應用程式伺服器。

### 開始之前

請先完成這兩個工作，然後再啟用 `ApplicationServer` 模組：

* 設定Nginx

* 安裝並設定Open Swoole v22擴充功能

### 設定Nginx

您的特定Commerce部署會決定如何設定Nginx。 一般而言，Nginx組態檔案預設為 `nginx.conf` 和會放置在下列其中一個目錄中： `/usr/local/nginx/conf`， `/etc/nginx`，或 `/usr/local/etc/nginx`. 另請參閱 [初學者指南](https://nginx.org/en/docs/beginners_guide.html) 有關設定Nginx的詳細資訊。

Nginx設定範例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### 安裝及設定Open Swool

若要在本機執行應用程式伺服器，請安裝Open Swoole v22擴充功能。 有多種方式可安裝此擴充功能。

## 執行應用程式伺服器

啟動應用程式伺服器：

```bash
bin/magento server:run
```

這個指令會在9501上啟動HTTP連線埠。 應用程式伺服器啟動後，連線埠9501就會變成所有GraphQL查詢的HTTP Proxy伺服器。

## 範例：安裝Open Swool (OSX)

此程式說明如何在PHP 8.2上為OSX系統安裝Open Swoole擴充功能。 這是安裝Open Swool擴充功能的數種方式之一。

您可以使用一個指令來安裝PHP (v22)的Open Swoole擴充功能以及此擴充功能所需的Composer套件。

### 安裝Open Swool

輸入：

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

在安裝期間，Adobe Commerce會顯示提示以啟用以下專案的支援： `openssl`， `mysqlnd`， `sockets`， `http2`、和 `postgres`. 輸入 `yes` 適用於所有選項，但 `postgres`.

### 確認安裝Open Swool

執行 `php -m | grep openswoole` 以確認已成功啟用擴充功能。

### Open Swool安裝的常見錯誤

Open Swool安裝期間發生的任何錯誤通常發生在 `pecl` 安裝階段。 典型錯誤包括遺失 `openssl.h` 和 `pcre2.h` 檔案。 若要解決這些錯誤，請確定這兩個套件已安裝在您的本機系統中。

* 檢查位置 `openssl` 藉由執行：

```bash
openssl version -d
```

這個命令會顯示以下位置的路徑： `openssl` 已安裝。

* 檢查位置 `pcre2` 藉由執行：

```bash
pcre2-config --prefix 
```

如果命令輸出指出遺失檔案，請使用Homebrew安裝遺失的套件：

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### 解決openssl的問題

若要解決以下相關問題： `openssl`，執行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

確認您使用的是本機的路徑 `dev` 環境。

#### 確認解決openssl相關問題

您可以再次執行以下命令，以檢查是否已解決與openssl相關的問題：

```bash
pecl install openswoole-22.0.0
```

#### 解決pcre2.h的問題

若要解決以下相關問題： `pcre2.h`，將連結 `pcre2.h` 您安裝的PHP擴充功能目錄的路徑。 您安裝的特定版本的PHP和 `pcr2.h` 會決定您應使用的指令的特定版本。
