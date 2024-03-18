---
title: GraphQL API的應用程式伺服器
description: 請依照這些指示，在您的Adobe Commerce部署中啟用GraphQL API的應用程式伺服器。
badgeCoreBeta: label="2.4.7測試版" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 9d5795400880a65947b1b90c8806b9dcb14aba23
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

# GraphQL API的應用程式伺服器

適用於GraphQL API的Commerce Application Server可讓Adobe Commerce維護Commerce GraphQL API請求中的狀態。 以Swoole擴充功能建置的應用程式伺服器，會以處理要求處理的工作者執行緒的流程運作。 應用程式伺服器可保留GraphQL API要求中的啟動載入應用程式狀態，進而增強要求處理和整體產品效能。 API要求會大幅提高效率。

應用程式伺服器僅在Adobe Commerce的雲端基礎結構入門和Pro專案上受支援。 它不適用於Magento Open Source專案。 Adobe不支援應用程式伺服器的內部部署。

## 應用程式伺服器架構概述

應用程式伺服器可維護Commerce GraphQL API請求之間的狀態，且無需啟動程式。 藉由跨程式共用應用程式狀態，GraphQL要求可大幅提高效率，最多將回應時間減少30%。

從延遲的角度來看，無共用PHP執行模型是一個挑戰，因為每個請求都需要架構的啟動安裝。 此啟動載入程式包括耗時的工作，例如讀取組態、設定啟動載入程式，以及建立服務類別物件。

將請求處理邏輯轉換為應用程式層級的事件回圈，似乎可解決在企業層級精簡請求處理的挑戰。 此方法可免除在請求執行生命週期期間進行啟動載入的需求。

## 使用應用程式伺服器的優點

應用程式伺服器可讓Adobe Commerce在連續的Commerce GraphQL API請求之間維持狀態。 跨請求共用應用程式狀態透過最小化處理開銷和最佳化請求處理來增強API請求效率。 因此，GraphQL要求回應時間最多可減少30%。

## 系統需求

執行「應用程式伺服器」需要下列專案：

* PHP 8.2或更高版本
* 已安裝Swool PHP擴充功能v5+
* 根據預期負載提供足夠的RAM和CPU

## 啟用應用程式伺服器

此 `ApplicationServer` 模組(`Magento/ApplicationServer/`)啟用GraphQL API的應用程式伺服器。 內部部署和雲端部署均支援應用程式伺服器。

## 在Cloud Pro上啟用應用程式伺服器

在Cloud Pro上部署應用程式伺服器之前，請先完成下列工作：

1. 確認已使用Adobe Commerce範本2.4.7版或更新版本，在Commerce Cloud上安裝Cloud。
1. 確保您的所有Commerce自訂和擴充功能都 [相容](https://developer.adobe.com/commerce/php/development/components/app-server/) 與Application Server。
1. 複製您的Commerce Cloud專案。
1. 如有必要，請調整&#39;application-server/nginx.conf.sample&#39;檔案中的設定。
1. 註解中的作用中&#39;web&#39;區段 `project_root/.magento.app.yaml` 檔案完成。
1. 取消註解以下的「Web」區段設定(在 `project_root/.magento.app.yaml` 包含應用程式伺服器啟動指令的檔案。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 使用以下命令將更新的檔案新增到Git索引：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 使用此命令提交您的變更：

   ```bash
   git commit -m "AppServer Enabled"
   ```

### 在Cloud Pro上部署應用程式伺服器

執行先決條件工作後，請使用下列命令部署「應用程式伺服器」：

```bash
git push
```

### 開始進行Cloud Starter部署之前

在Cloud Starter上部署應用程式伺服器之前，請先完成下列工作：

1. 確認已使用Adobe Commerce範本2.4.7版或更新版本，在Commerce Cloud上安裝Cloud。
1. 請確定您所有的Commerce自訂專案和擴充功能都與應用程式伺服器相容。
1. 確認 `CRYPT_KEY` 環境變數已針對您的執行個體設定。 您可以在雲端專案入口網站（入門UI）上檢視此變數的狀態。
1. 複製您的Commerce Cloud專案。
1. 重新命名 `application-server/.magento/.magento.app.yaml.sample` 至 `application-server/.magento/.magento.app.yaml` 並視需要調整.magento.app.yaml中的設定。
1. 取消註解下列路由在 `project_root/.magento/routes.yaml` 要重新導向的檔案 `/graphql` 應用程式伺服器的流量。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 使用下列命令將更新的檔案新增到Git索引中：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 使用此命令提交您的變更：

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
> 確定您在根目錄中的所有自訂設定 `.magento.app.yaml` 檔案已適當移轉至 `application-server/.magento/.magento.app.yaml` 檔案。 一旦 `application-server/.magento/.magento.app.yaml` 檔案會新增至您的專案，因此您除了維護根以外，也應維護它 `.magento.app.yaml` 檔案。
> 例如，如果您需要 [設定rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) 或 [管理Web屬性](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 您應該將相同的設定新增到 `application-server/.magento/.magento.app.yaml` 以及。

### 在雲端入門程式上部署應用程式伺服器

完成 [必備條件](#before-you-begin-a-cloud-starter-deployment)，使用此命令部署應用程式伺服器：

```bash
git push
```

### 驗證Cloud Starter是否啟用應用程式伺服器

1. 針對您的執行個體執行GraphQL查詢或突變，以確認 `graphql` 端點可供存取。 例如：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   預期的回應應類似於以下範例：

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. 使用SSH存取您的雲端例項。 此 `project_root/var/log/application-server.log` 應該包含每個GraphQL請求的新記錄記錄。

1. 您也可以透過執行以下命令來檢查Application Server是否正在執行：

   ```bash
   ps aux|grep php
   ```

   您應該會看到 `bin/magento server:run` 使用多個執行緒的處理。

如果這些驗證步驟成功，應用程式伺服器就會執行並提供服務 `/graphql` 要求。


## 啟用應用程式伺服器內部部署

此 `ApplicationServer` 模組(`Magento/ApplicationServer/`)啟用GraphQL API的應用程式伺服器。

在本機執行Application Server需要安裝Swoole延伸模組，並對部署的NGINX組態檔進行微幅變更。

### 開始內部部署之前

請先完成這兩個工作，然後再啟用 `ApplicationServer` 模組：

* 設定Nginx

* 安裝及設定Swoole v5+擴充功能

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

### 安裝和設定Swool

若要在本機執行應用程式伺服器，請安裝Swoole擴充功能（v5.0或更新版本）。 有多種方式可安裝此擴充功能。

## 執行應用程式伺服器

啟動應用程式伺服器：

```bash
bin/magento server:run
```

這個指令會在9501上啟動HTTP連線埠。 應用程式伺服器啟動後，連線埠9501就會變成所有GraphQL查詢的HTTP Proxy伺服器。

## 範例：安裝Swoole (OSX)

此程式說明如何在PHP 8.2上為OSX系統安裝Swoole擴充功能。 這是安裝Swoole擴充功能的數種方式之一。

### 安裝Swool

輸入：

```bash
pecl install swoole
```

在安裝期間，Adobe Commerce會顯示提示以啟用以下專案的支援： `openssl`， `mysqlnd`， `sockets`， `http2`、和 `postgres`. 輸入 `yes` 適用於所有選項，但 `postgres`.

### 確認安裝Swool

執行 `php -m | grep swoole` 以確認已成功啟用擴充功能。

### Swoole安裝的常見錯誤

Swool安裝期間發生的任何錯誤通常發生在 `pecl` 安裝階段。 典型錯誤包括遺失 `openssl.h` 和 `pcre2.h` 檔案。 若要解決這些錯誤，請確定這兩個套件已安裝在您的本機系統中。

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
pecl install swoole
```

#### 解決pcre2.h的問題

若要解決以下相關問題： `pcre2.h`，將連結 `pcre2.h` 您安裝的PHP擴充功能目錄的路徑。 您安裝的特定版本的PHP和 `pcr2.h` 會決定您應使用的指令的特定版本。

### 確認應用程式伺服器執行中

若要確認應用程式伺服器正在您的部署中執行，請執行此命令：

```bash
ps aux | grep php
```

確認Application Server正在執行的其他方法包括：

* 檢查 `/var/log/application-server.log` 與已處理GraphQL請求相關的專案檔案。
* 嘗試連線到Application Server執行所在的HTTP連線埠。 例如： `curl -g 'http://localhost:9501/graph`.

### 確認應用程式伺服器正在處理GraphQL請求

應用程式伺服器新增 `X-Backend` 包含值的回應標頭 `graphql_server` 至其處理的每個請求。 若要檢查應用程式伺服器是否已處理要求，請檢查此回應標頭。

### 確認與應用程式伺服器的擴充和自訂相容性

擴充功能開發人員和商家應該先確認其擴充功能和自訂程式碼符合中說明的技術准則。 [技術准則](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

在程式碼評估期間請考量下列准則：

* 服務類別(即提供行為但不提供資料的類別，例如 `EventManager`)不應該有可變狀態。
* 避免暫時耦合。

## 停用應用程式伺服器

根據伺服器是在內部部署還是雲端部署中執行，停用應用程式伺服器的程式會有所不同。

### 在雲端啟動器上停用應用程式伺服器

1. 移除包含在「 」中的任何新檔案和任何其他程式碼變更。 `AppServer Enabled` 在部署準備期間進行認可。

1. 使用此命令確認您的變更：

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 使用此命令部署這些變更：

   ```bash
   git push
   ```

### 停用應用程式伺服器

1. 取消註解 `/graphql` 部分 `nginx.conf` 啟用Application Server時新增的檔案。
1. 重新啟動nginx。

此停用應用程式伺服器的方法對於快速測試或比較效能很有用。

### 確認已停用應用程式伺服器

若要確認GraphQL請求正在由處理 `php-fpm` 輸入以下命令，而不是「應用程式伺服器」： `ps aux | grep php`.

停用應用程式伺服器之後：

* `bin/magento server:run` 為非使用中。
* `var/log/application-server.log` 在GraphQL請求後不包含任何專案。

## PHP應用程式伺服器的整合與功能測試

擴充功能開發人員可執行兩項整合測試，以驗證擴充功能與應用程式伺服器的相容性： `GraphQlStateTest` 和 `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` 會偵測共用物件中不應重複用於多個請求的狀態。

此測試的目的是偵測服務物件中由產生的狀態變更。 `ObjectManager`. 此測試會執行兩次相同的GraphQL查詢，並比較第二次查詢前後的服務物件狀態。

#### GraphQlStateTest失敗和可能的補救

* **無法新增、略過或篩選清單**. 如果您遇到錯誤，指出新增、略過或篩選清單是不安全的，請考慮是否能夠以向後相容的方式重構類別，以使用具有可變狀態的服務類別的工廠。

* **類別呈現可變狀態**. 如果類別本身呈現可變狀態，請嘗試重寫您的程式碼以規避此狀態。 如果基於效能原因需要可變狀態，則實作 `ResetAfterRequestInterface` 和使用 `_resetState()` 將物件重設為初始建構狀態。

* **在初始化訊息之前不可存取輸入的屬性$x**. 這類訊息的失敗表示建構函式尚未初始化指定的屬性。 這是暫時耦合的形式，因為物件在初始建構後就無法使用。 即使屬性是私有的，也會發生這種耦合，因為從屬性中擷取資料的收集器正在使用PHP反射特徵。 在這種情況下，請嘗試重構類別以避免暫時耦合併避免可變狀態。 如果該重構無法解決失敗，您可以將屬性型別變更為空型別，以便將其初始化為空值。  如果屬性是陣列，請嘗試將屬性初始化為空陣列。

執行 `GraphQlStateTest` 透過執行 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` 會尋找所有實作的類別 `ResetAfterRequestInterface` 並驗證 `_resetState()` 方法會將物件的狀態傳回至與建構物件後保持相同的狀態 `ObjectManager`.  此測試會建立服務物件，其包含 `ObjectManager`，然後複製該物件，呼叫 `_resetState()`，然後比較兩個物件。 測試不會在物件例項化與之間呼叫任何方法 `_resetState()`，因此不會確認重設任何可變狀態。 它會發現中的錯誤或拼寫錯誤問題 `_resetState()` 可能會將州設定為與原本不同的狀態。

#### ResetAfterRequestTest失敗和可能的修復

* **類別具有不一致的屬性值**. 如果此測試失敗，請檢查類別是否已變更，結果是在建構後的物件與建構後的物件具有不同的屬性值 `_resetState()` 方法稱為。 如果您使用的類別不包含 `_resetState()` 方法本身，然後檢查實作它的超類別的類別階層。

* **在初始化訊息之前不可存取輸入的屬性$x**. 此問題也會發生在 `GraphQlStateTest`.

  執行 `ResetAfterRequestTest` 透過執行： `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### 功能測試

擴充功能開發人員在部署應用程式伺服器時，應執行GraphQL的WebAPI功能測試，以及GraphQL的任何自訂自動化或手動功能測試。 這些功能測試可協助開發人員識別潛在的錯誤或相容性問題。
