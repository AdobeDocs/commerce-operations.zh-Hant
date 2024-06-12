---
title: GraphQL應用程式伺服器
description: 請依照這些指示，在您的Adobe Commerce部署中啟用GraphQL應用程式伺服器。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c2f48db87f40498a84b2bf41569bb46202565701
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---


# GraphQL應用程式伺服器

Commerce GraphQL應用程式伺服器可讓Adobe Commerce維護Commerce GraphQL API請求中的狀態。 GraphQL Application Server （以Swoole擴充功能為基礎）會以具有工作者執行緒的處理程式方式運作，以處理要求處理。 GraphQL Application Server可保留GraphQL API請求中的啟動載入應用程式狀態，藉此增強請求處理和整體產品效能。 API要求會大幅提高效率。

GraphQL Application Server僅適用於Adobe Commerce。 它無法用於Magento Open Source。 您必須 [提交Adobe Commerce支援](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) 票證以在Pro專案上啟用GraphQL Application Server。

>[!NOTE]
>
>GraphQL應用程式伺服器目前與不相容 [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). 目前使用的雲端基礎結構客戶上的Adobe Commerce [!DNL AWS S3] 的 [遠端儲存](../configuration/remote-storage/cloud-support.md) 在Adobe於2024年稍後發行Hotfix之前，無法使用GraphQL應用程式伺服器。

## 架構

GraphQL Application Server可維護Commerce GraphQL API請求之間的狀態，且無需啟動程式。 藉由跨程式共用應用程式狀態，GraphQL要求可大幅提高效率，最多將回應時間減少30%。

從延遲的角度來看，無共用PHP執行模型是一個挑戰，因為每個請求都需要架構的啟動安裝。 此啟動載入程式包括耗時的工作，例如讀取組態、設定啟動載入程式，以及建立服務類別物件。

將請求處理邏輯轉換為應用程式層級的事件回圈，似乎可解決在企業層級精簡請求處理的挑戰。 此方法可免除在請求執行生命週期期間進行啟動載入的需求。

## 優點

GraphQL應用程式伺服器可讓Adobe Commerce在連續的Commerce GraphQL API請求之間維持狀態。 跨請求共用應用程式狀態透過最小化處理開銷和最佳化請求處理來增強API請求效率。 因此，GraphQL要求回應時間最多可減少30%。

## 系統需求

執行GraphQL Application Server需要下列專案：

* PHP 8.2或更高版本
* 已安裝Swool PHP擴充功能v5+
* 根據預期負載提供足夠的RAM和CPU

## 在雲端基礎結構上啟用和部署

此 `ApplicationServer` 模組(`Magento/ApplicationServer/`)啟用GraphQL應用程式伺服器。

### 啟用Pro專案

>[!NOTE]
>
>「應用程式伺服器」是Cloud Pro例項上的選擇加入功能。 若要啟用該功能，請提交支援要求。

在Pro專案上啟用「應用程式伺服器」功能後，請先完成下列步驟，再部署GraphQL Application Server：

1. 使用來自的雲端範本，在雲端基礎結構上部署Adobe Commerce [2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. 確認您所有的Commerce自訂專案和擴充功能皆為 [相容](https://developer.adobe.com/commerce/php/development/components/app-server/) 與GraphQL Application Server整合。
1. 複製您的Commerce Cloud專案。
1. 如有必要，請調整&#39;application-server/nginx.conf.sample&#39;檔案中的設定。
1. 註解中的作用中&#39;web&#39;區段 `project_root/.magento.app.yaml` 檔案完成。
1. 取消註解以下的「Web」區段設定(在 `project_root/.magento.app.yaml` 包含GraphQL應用程式伺服器的檔案 `start` 命令。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 確定 `/application-server/start.sh` 可執行下列命令：

   ```bash
   chmod +x application-server/start.sh
   ```

1. 使用以下命令將更新的檔案新增到Git索引：

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. 使用此命令提交您的變更：

   ```bash
   git commit -m "AppServer Enabled"
   ```

### 部署Pro專案

完成啟用步驟後，將變更推送至您的Git存放庫以部署GraphQL應用程式伺服器：

```bash
git push
```

### 啟用入門專案

在入門專案上部署GraphQL Application Server前，請先完成下列步驟：

1. 使用來自的雲端範本，在雲端基礎結構上部署Adobe Commerce [2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. 確認您所有的Commerce自訂專案和擴充功能都與GraphQL Application Server相容。
1. 確認 `CRYPT_KEY` 環境變數已針對您的執行個體設定。 您可以在雲端專案入口網站（入門UI）上檢視此變數的狀態。
1. 複製您的Commerce Cloud專案。
1. 重新命名 `application-server/.magento/.magento.app.yaml.sample` 至 `application-server/.magento/.magento.app.yaml` 並視需要調整.magento.app.yaml中的設定。
1. 取消註解下列路由在 `project_root/.magento/routes.yaml` 要重新導向的檔案 `/graphql` GraphQL應用程式伺服器的流量。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 將更新的檔案新增至Git索引：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 提交您的變更：

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>確定根目錄中的所有自訂設定 `.magento.app.yaml` 檔案已適當移轉至 `application-server/.magento/.magento.app.yaml` 檔案。 在 `application-server/.magento/.magento.app.yaml` 檔案會新增至您的專案，因此您除了維護根以外，也應維護它 `.magento.app.yaml` 檔案。 例如，如果您需要 [設定rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) 或 [管理Web屬性](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 您應該將相同的設定新增到 `application-server/.magento/.magento.app.yaml` 以及。

### 部署入門專案

完成啟用後 [步驟](#before-you-begin-a-cloud-starter-deployment)，推送變更至您的Git存放庫以部署GraphQL Application Server：

```bash
git push
```

### 驗證雲端專案是否啟用

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

1. 您也可以執行下列命令，檢查GraphQL Application Server是否正在執行：

   ```bash
   ps aux|grep php
   ```

   您應該會看到 `bin/magento server:run` 使用多個執行緒的處理。

如果這些驗證步驟成功，GraphQL Application Server就會執行並提供服務 `/graphql` 要求。

## 啟用內部部署專案

此 `ApplicationServer` 模組(`Magento/ApplicationServer/`)啟用適用於GraphQL API的GraphQL應用程式伺服器。

在本機執行GraphQL Application Server需要安裝Swoole延伸模組，並對部署的Nginx設定檔進行微幅變更。

### 必要條件

在啟用 `ApplicationServer` 模組：

* 設定Nginx
* 安裝及設定Swoole v5+擴充功能

#### 設定Nginx

您特定的Commerce部署決定了如何設定Nginx。 一般而言，Nginx組態檔案預設為 `nginx.conf` 和會放置在下列其中一個目錄中： `/usr/local/nginx/conf`， `/etc/nginx`，或 `/usr/local/etc/nginx`. 另請參閱 [初學者指南](https://nginx.org/en/docs/beginners_guide.html) 有關設定Nginx的詳細資訊。

Nginx設定範例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### 安裝和設定Swool

若要在本機執行GraphQL Application Server，請安裝Swoole擴充功能（v5.0或更新版本）。 有多種方式可安裝此擴充功能。

下列程式說明如何在OSX系統上安裝PHP 8.2的Swoole擴充功能。 這是安裝Swoole擴充功能的數種方式之一。

```bash
pecl install swoole
```

在安裝期間，Adobe Commerce會顯示提示以啟用以下專案的支援： `openssl`， `mysqlnd`， `sockets`， `http2`、和 `postgres`. 輸入 `yes` 適用於所有選項，但 `postgres`.

### 驗證Swool安裝

確認擴充功能已成功啟用：

```bash
php -m | grep swoole
```

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

### 執行GraphQL應用程式伺服器

啟動GraphQL應用程式伺服器：

```bash
bin/magento server:run
```

這個指令會在9501上啟動HTTP連線埠。 GraphQL應用程式伺服器啟動後，連線埠9501就會變成所有GraphQL查詢的HTTP Proxy伺服器。

若要確認GraphQL Application Server正在您的部署中執行：

```bash
ps aux | grep php
```

確認GraphQL Application Server正在執行的其他方法包括：

* 檢查 `/var/log/application-server.log` 與已處理GraphQL請求相關的專案檔案。
* 嘗試連線到GraphQL Application Server執行所在的HTTP連線埠。 例如： `curl -g 'http://localhost:9501/graph`.

### 確認正在處理GraphQL請求

GraphQL應用程式伺服器新增 `X-Backend` 包含值的回應標頭 `graphql_server` 至其處理的每個請求。 若要檢查要求是否已由GraphQL應用程式伺服器處理，請檢查此回應標頭。

### 確認擴充功能和自訂相容性

擴充功能開發人員和商家應該先確認其擴充功能和自訂程式碼符合中說明的技術准則。 [技術准則](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

在程式碼評估期間請考量下列准則：

* 服務類別(即提供行為但不提供資料的類別，例如 `EventManager`)不應該有可變狀態。
* 避免暫時耦合。

## 停用GraphQL應用程式伺服器

停用GraphQL Application Server的程式會因伺服器是在內部部署或雲端部署中執行而有所不同。

### 停用GraphQL Application Server （雲端）

1. 移除包含在「 」中的任何新檔案和任何其他程式碼變更。 `AppServer Enabled` 在部署準備期間進行認可。

1. 使用此命令確認您的變更：

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 使用此命令部署這些變更：

   ```bash
   git push
   ```

### 停用GraphQL應用程式伺服器（內部部署）

1. 取消註解 `/graphql` 部分 `nginx.conf` 啟用GraphQL應用程式伺服器時新增的檔案。
1. 重新啟動nginx。

此停用GraphQL Application Server的方法對於快速測試或比較效能很有用。

### 確認GraphQL Application Server已停用

若要確認GraphQL請求正在由處理 `php-fpm` 輸入以下命令，而非GraphQL Application Server： `ps aux | grep php`.

停用GraphQL Application Server之後：

* `bin/magento server:run` 為非使用中。
* `var/log/application-server.log` 在GraphQL請求後不包含任何專案。

## GraphQL Application Server的整合和功能測試

擴充功能開發人員可以執行兩項整合測試，以驗證擴充功能與GraphQL Application Server的相容性： `GraphQlStateTest` 和 `ResetAfterRequestTest`.

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

擴充功能開發人員在部署GraphQL Application Server時，應執行GraphQL的WebAPI功能測試，以及GraphQL的任何自訂自動化或手動功能測試。 這些功能測試可協助開發人員識別潛在的錯誤或相容性問題。

#### 狀態監視器模式

執行功能測試（或手動測試）時，應用程式伺服器可以使用 `--state-monitor mode` 啟用以協助尋找無意中重複使用狀態的類別。 正常啟動應用程式伺服器，但新增 `--state-monitor` 引數。

```
bin/magento server:run --state-monitor
```

處理完每個請求後，新檔案會新增至 `tmp` 目錄，例如： `var/tmp/StateMonitor-thread-output-50-6nmxiK`. 完成測試後，這些檔案可與 `bin/magento server:state-monitor:aggregate-output` 指令，會建立兩個合併的檔案，一個在 `XML` 和一個 `JSON`.

範例：

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

您可以使用檢視XML或JSON的任何工具來檢查這些檔案，這些工具會顯示服務物件的修改屬性，例如GraphQlStateTest。 此 `--state-monitor` 模式使用與GraphQlStateTest相同的略過清單和篩選清單。

>[!NOTE]
>
>請勿使用 `--state-monitor` 生產模式。 它僅供開發和測試使用。 它會建立許多輸出檔案，而且執行速度會比平常慢。

>[!NOTE]
>
>`--state-monitor` 與PHP版本不相容 `8.3.0` - `8.3.4` 由於PHP記憶體回收器中的錯誤。 如果您使用的是PHP 8.3，則必須升級到 `8.3.5` 或更新以使用此功能。
