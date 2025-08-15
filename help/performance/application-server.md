---
title: GraphQL應用程式伺服器
description: 請依照這些指示，在您的Adobe Commerce部署中啟用GraphQL應用程式伺服器。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 8427460cd11169ffe7dd2d4ba0cc1fdaea513702
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 0%

---


# GraphQL應用程式伺服器

Commerce GraphQL應用程式伺服器可讓Adobe Commerce維護Commerce GraphQL API請求中的狀態。 GraphQL Application Server （以Swoole擴充功能為基礎）會以具有工作者執行緒的處理程式方式運作，以處理要求處理。 GraphQL Application Server可保留GraphQL API請求中的啟動載入應用程式狀態，藉此增強請求處理和整體產品效能。 API要求會大幅提高效率。

GraphQL Application Server僅適用於Adobe Commerce。 它不適用於Magento Open Source。 對於Cloud Pro專案，您必須[提交Adobe Commerce支援](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)票證，才能啟用GraphQL應用程式伺服器。

>[!NOTE]
>
>GraphQL Application Server目前與[[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/)不相容。 雲端基礎結構上的Adobe Commerce客戶目前將[!DNL AWS S3]用於[遠端儲存空間](../configuration/remote-storage/cloud-support.md)，無法使用GraphQL應用程式伺服器。

## 架構

GraphQL Application Server可維護Commerce GraphQL API請求之間的狀態，且無需啟動程式。 藉由跨程式共用應用程式狀態，GraphQL要求可大幅提高效率，最多將回應時間減少30%。

從延遲的角度來看，無共用PHP執行模型是一個挑戰，因為每個請求都需要架構的啟動安裝。 此啟動載入程式包括耗時的工作，例如讀取組態、設定啟動載入程式，以及建立服務類別物件。

將請求處理邏輯轉換為應用程式層級的事件回圈，似乎可解決在企業層級精簡請求處理的挑戰。 此方法可免除在請求執行生命週期期間進行啟動載入的需求。

## 優點

GraphQL應用程式伺服器可讓Adobe Commerce在連續的Commerce GraphQL API請求之間維持狀態。 跨請求共用應用程式狀態透過最小化處理開銷和最佳化請求處理來增強API請求效率。 因此，GraphQL要求回應時間最多可減少30%。

## 系統需求

執行GraphQL Application Server需要下列專案：

* Commerce 2.4.7+版
* PHP 8.2或更高版本
* 已安裝Swool PHP擴充功能v5+
* 根據預期負載提供足夠的RAM和CPU

## 在雲端基礎結構上啟用和部署

`ApplicationServer`模組(`Magento/ApplicationServer/`)啟用GraphQL應用程式伺服器。

### 啟用Pro專案

>[!NOTE]
>
>「應用程式伺服器」是Cloud Pro例項上的選擇加入功能。 若要啟用該功能，請提交支援要求。

在Pro專案上啟用「應用程式伺服器」功能後，請先完成下列步驟，再部署GraphQL Application Server：

1. 從[2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)使用雲端範本，在雲端基礎結構上部署Adobe Commerce。
1. 確定您所有的Commerce自訂專案和擴充功能都與GraphQL Application Server [相容](https://developer.adobe.com/commerce/php/development/components/app-server/)。
1. 複製Commerce Cloud專案。
1. 如有必要，請調整&#39;application-server/nginx.conf.sample&#39;檔案中的設定。
1. 完全註解`project_root/.magento.app.yaml`檔案中的作用中&#39;web&#39;區段。
1. 取消註解`project_root/.magento.app.yaml`檔案中包含GraphQL應用程式伺服器`start`命令的以下&#39;web&#39;區段設定。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 執行下列命令，確定`/application-server/start.sh`是可執行的命令：

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

1. 從[2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)使用雲端範本，在雲端基礎結構上部署Adobe Commerce。
1. 確認您所有的Commerce自訂專案和擴充功能都與GraphQL Application Server相容。
1. 確認已為您的執行個體設定`CRYPT_KEY`環境變數。 您可以在Cloud Console上檢查此變數的狀態。
1. 複製Commerce Cloud專案。
1. 將`application-server/.magento/.magento.app.yaml.sample`重新命名為`application-server/.magento/.magento.app.yaml`，並視需要調整.magento.app.yaml中的設定。
1. 取消註解`project_root/.magento/routes.yaml`檔案中的下列路由設定，將`/graphql`流量重新導向至GraphQL應用程式伺服器。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 取消註解`files`檔案中的`.magento/services.yaml`區段。

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. 取消註解`TEMPORARY SHARED MOUNTS`檔案中裝載組態的`.magento.app.yaml`部分。

   ```yaml
   "var_shared":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc_shared":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media_shared":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static_shared":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. 將更新的檔案新增至Git索引：

   ```bash
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. 提交您的變更並推送以觸發部署：

   ```bash
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. 使用SSH登入遠端雲端環境（_不是_ `application-server`應用程式）：

   ```bash
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. 將資料從本機掛載同步到共用掛載：

   ```bash
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. 註解`DEFAULT MOUNTS`檔案中裝載組態的`TEMPORARY SHARED MOUNTS`和`.magento.app.yaml`部分。

   ```yaml
   #"var": "shared:files/var"
   #"app/etc": "shared:files/etc"
   #"pub/media": "shared:files/media"
   #"pub/static": "shared:files/static"
   
   #"var_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "var"
   #"app/etc_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "etc"
   #"pub/media_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "media"
   #"pub/static_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "static"
   ```

1. 取消註解`OLD LOCAL MOUNTS`檔案中裝載組態的`SHARED MOUNTS`和`.magento.app.yaml`部分。

   ```yaml
   "var_old": "shared:files/var"
   "app/etc_old": "shared:files/etc"
   "pub/media_old": "shared:files/media"
   "pub/static_old": "shared:files/static"
   
   "var":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. 將更新的檔案新增到Git索引、認可變更並推播以觸發部署：

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. 確定來自`*_old`目錄的檔案存在於實際目錄中。

1. 清理舊的本機掛載：

   ```bash
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. 註解`OLD LOCAL MOUNTS`檔案中裝載組態的`.magento.app.yaml`部分。

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. 將更新的檔案新增到Git索引、認可變更並推播以觸發部署：

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>確定您的根`.magento.app.yaml`檔案中的所有自訂設定都已適當地移轉至`application-server/.magento/.magento.app.yaml`檔案。 將`application-server/.magento/.magento.app.yaml`檔案新增至專案後，除了根`.magento.app.yaml`檔案之外，您還應維護該檔案。 例如，如果您需要[設定RabbitMQ服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq)或[管理Web屬性](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property)，您也應該將相同的設定新增到`application-server/.magento/.magento.app.yaml`。

### 驗證雲端專案是否啟用

1. 對您的執行個體執行GraphQL查詢或突變，以確認`graphql`端點可存取。 例如：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   預期的回應應類似於以下範例：

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. 使用SSH存取您的雲端例項。 `project_root/var/log/application-server.log`應該包含每個GraphQL要求的新記錄記錄。

1. 您也可以執行下列命令，檢查GraphQL Application Server是否正在執行：

   ```bash
   ps aux|grep php
   ```

   您應該會看到含有多個執行緒的`bin/magento server:run`處理序。

如果這些驗證步驟成功，GraphQL Application Server就會執行並提供`/graphql`要求。

## 啟用內部部署專案

`ApplicationServer`模組(`Magento/ApplicationServer/`)可為GraphQL API啟用GraphQL應用程式伺服器。

在本機執行GraphQL Application Server需要安裝Swoole延伸模組，並對部署的Nginx設定檔進行微幅變更。

### 先決條件

在啟用`ApplicationServer`模組之前，請先完成下列步驟：

* 設定Nginx
* 安裝及設定Swoole v5+擴充功能

#### 設定Nginx

您特定的Commerce部署決定了如何設定Nginx。 一般而言，Nginx組態檔預設名為`nginx.conf`，並放置在下列其中一個目錄中： `/usr/local/nginx/conf`、`/etc/nginx`或`/usr/local/etc/nginx`。 如需設定Nginx的詳細資訊，請參閱&#x200B;_[初學者指南](https://nginx.org/en/docs/beginners_guide.html)_。

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

在安裝期間，Adobe Commerce會顯示提示以啟用`openssl`、`mysqlnd`、`sockets`、`http2`和`postgres`的支援。 輸入`yes`以取得除`postgres`以外的所有選項。

### 驗證Swool安裝

確認擴充功能已成功啟用：

```bash
php -m | grep swoole
```

### Swoole安裝的常見錯誤

在Swoole安裝期間發生的任何錯誤通常發生在`pecl`安裝階段。 典型的錯誤包括遺失`openssl.h`和`pcre2.h`檔案。 若要解決這些錯誤，請確定這兩個套件已安裝在您的本機系統中。

* 執行，以檢查`openssl`的位置：

```bash
openssl version -d
```

這個命令顯示`openssl`的安裝路徑。

* 執行，以檢查`pcre2`的位置：

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

若要解決與`openssl`相關的問題，請執行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

確認您使用的是本機`dev`環境的路徑。

#### 確認解決openssl相關問題

您可以再次執行以下命令，以檢查是否已解決與openssl相關的問題：

```bash
pecl install swoole
```

#### 解決pcre2.h的問題

若要解決與`pcre2.h`相關的問題，請將`pcre2.h`路徑同步連結到您安裝的PHP延伸模組目錄。 您安裝的特定版本PHP和`pcr2.h`決定了您應該使用的指令的特定版本。

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

* 檢查`/var/log/application-server.log`檔案中是否有與已處理GraphQL要求相關的專案。
* 嘗試連線到GraphQL Application Server執行所在的HTTP連線埠。 例如： `curl -g 'http://localhost:9501/graph`。

### 確認正在處理GraphQL請求

GraphQL Application Server將值為`X-Backend`的`graphql_server`回應標頭新增至其處理的每個要求。 若要檢查GraphQL應用程式伺服器是否已處理要求，請檢查此回應標頭。

### 確認擴充功能和自訂相容性

擴充功能開發人員和商家應該先確認其擴充功能和自訂程式碼符合&#x200B;_[技術准則](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_&#x200B;中所述的准則。

在程式碼評估期間請考量下列准則：

* 服務類別（也就是提供行為但不提供資料的類別，例如`EventManager`）不應該有可變狀態。
* 避免暫時耦合。

## 停用GraphQL應用程式伺服器

停用GraphQL Application Server的程式會因伺服器是在內部部署或雲端部署中執行而有所不同。

### 停用GraphQL Application Server （雲端）

1. 移除您在準備部署期間在`AppServer Enabled`認可中包含的任何新檔案和任何其他程式碼變更。

1. 使用此命令確認您的變更：

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 使用此命令部署這些變更：

   ```bash
   git push
   ```

### 停用GraphQL應用程式伺服器（內部部署）

1. 請註解您在啟用GraphQL應用程式伺服器時新增的`/graphql`檔案的`nginx.conf`區段。
1. 重新啟動nginx。

此停用GraphQL應用程式伺服器的方法有助於快速測試或比較效能。

### 確認GraphQL Application Server已停用

若要確認`php-fpm`正在處理GraphQL要求而非GraphQL應用程式伺服器，請輸入以下命令： `ps aux | grep php`。

停用GraphQL Application Server之後：

* `bin/magento server:run`為非作用中。
* 在GraphQL要求之後，`var/log/application-server.log`不包含任何專案。

## GraphQL Application Server的整合和功能測試

擴充功能開發人員可執行兩項整合測試，以驗證與GraphQL Application Server的擴充功能相容性： `GraphQlStateTest`和`ResetAfterRequestTest`。

### GraphQlStateTest

`GraphQlStateTest`會偵測共用物件中不應重複用於多個要求的狀態。

此測試的目的是偵測`ObjectManager`產生的服務物件中的狀態變更。 此測試會執行兩次相同的GraphQL查詢，並比較第二次查詢前後的服務物件狀態。

#### GraphQlStateTest失敗和可能的補救

* **無法新增、略過或篩選清單**。 如果您看到有關新增、略過或篩選清單的錯誤，請考慮是否可以向後相容的方式重構類別，以使用具有可變狀態的服務類別之工廠。

* **類別呈現可變狀態**。 如果類別本身呈現可變狀態，請嘗試重寫您的程式碼以規避此狀態。 如果因為效能原因需要可變狀態，則實作`ResetAfterRequestInterface`並使用`_resetState()`將物件重設為初始建構狀態。

* **在初始化訊息**&#x200B;之前，不能存取Typed屬性$x。 這類訊息的失敗表示建構函式尚未初始化指定的屬性。 這是暫時耦合的形式，因為物件在初始建構後就無法使用。 即使屬性是私有的，也會發生這種耦合，因為從屬性中擷取資料的收集器正在使用PHP反射特徵。 在這種情況下，請嘗試重構類別以避免暫時耦合併避免可變狀態。 如果該重構無法解決失敗，您可以將屬性型別變更為空型別，以便將其初始化為空值。  如果屬性是陣列，請嘗試將屬性初始化為空陣列。

執行`GraphQlStateTest`以執行`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`。

### ResetAfterRequestTest

`ResetAfterRequestTest`會尋找所有實作`ResetAfterRequestInterface`的類別，並驗證`_resetState()`方法是否會將物件的狀態傳回至`ObjectManager`建構後所保持的狀態。  此測試會建立具有`ObjectManager`的服務物件，然後複製該物件，呼叫`_resetState()`，然後比較兩個物件。 測試未呼叫物件例項化與`_resetState()`之間的任何方法，因此不會確認重設任何可變狀態。 它確實發現`_resetState()`中的錯誤或錯字可能會將狀態設定為與原來不同的狀態。

#### ResetAfterRequestTest失敗和可能的修復

* **類別的屬性值**&#x200B;不一致。 如果此測試失敗，請檢查類別是否已變更，結果是在建構之後物件與呼叫`_resetState()`方法之後物件具有不同的屬性值。 如果您正在處理的類別不包含`_resetState()`方法本身，請檢查類別階層中實作它的超類別。

* **在初始化訊息**&#x200B;之前，不能存取Typed屬性$x。 `GraphQlStateTest`也會發生此問題。

  執行`ResetAfterRequestTest`以執行`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`。

### 功能測試

部署GraphQL Application Server時，擴充功能開發人員應執行WebAPI功能測試，以及GraphQL的任何自訂自動化或手動功能測試。 這些功能測試可協助開發人員識別潛在的錯誤或相容性問題。

#### 狀態監視器模式

執行功能測試（或手動測試）時，GraphQL Application Server可在啟用`--state-monitor mode`的情況下執行，以協助尋找無意中重複使用狀態的類別。 正常啟動應用程式伺服器，但新增`--state-monitor`引數除外。

```
bin/magento server:run --state-monitor
```

處理完每個要求後，新檔案會新增至`tmp`目錄，例如： `var/tmp/StateMonitor-thread-output-50-6nmxiK`。 完成測試後，這些檔案可以與`bin/magento server:state-monitor:aggregate-output`命令合併，這會建立兩個合併的檔案，一個在`XML`，一個在`JSON`。

範例：

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

您可以使用檢視XML或JSON的任何工具來檢查這些檔案，這些工具會顯示`GraphQlStateTest`等服務物件的修改屬性。 `--state-monitor`模式使用與GraphQlStateTest相同的略過清單和篩選清單。

>[!NOTE]
>
>請勿在生產環境中使用`--state-monitor`模式。 它僅供開發和測試使用。 它會建立許多輸出檔案，而且執行速度比正常慢。

>[!NOTE]
>
>由於PHP記憶體回收行程發生錯誤，`--state-monitor`與PHP版本`8.3.0` - `8.3.4`不相容。 如果您使用PHP 8.3，您必須升級至`8.3.5`或更新版本才能使用此功能。
