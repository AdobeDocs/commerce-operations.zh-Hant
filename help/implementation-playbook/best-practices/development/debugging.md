---
title: 偵錯最佳實務
description: 瞭解解決常見Adobe Commerce開發問題的技巧。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Adobe Commerce的除錯最佳實務

本主題說明系統和有效地偵錯Adobe Commerce架構的方式。 目標是協助您快速找到問題的根源，並將調查時間縮到最短。

## 疑難排解：常見問題

本節說明您在開發期間可能遇到的最常見問題。

### 快取

- 在進一步調查之前排清快取
- 考慮APC快取、CDN、Varnish、產生的程式碼以及 `var/view_preprocessed` 和 `pub/static/` 目錄
- 排清快取或修改程式碼後，停止並重新啟動佇列處理常式

以下程式碼範例提供與管理快取相關的實用命令（請勿在生產環境中執行）：

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### 索引資料

如果問題可能與索引相關，請重新索引所有內容。 除錯索引資料通常發生在非生產環境中。 在生產環境中，您可能需要在重新索引之前調查索引未對齊的原因。 故障狀態的特徵可以告訴您問題的起源。

### 作曲者

由於分支變更或在先前的偵錯工作中編輯的核心檔案，因此您的程式碼可能已過時。 若要消除潛在問題，請執行以下命令：

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### 產生的內容

在偵錯JS、CSS、影像、翻譯和其他檔案中產生的內容之前，請先重新建置前端檔案。

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### 開發人員模式

請確定您的本機安裝位於 `developer` 模式。

### 新模組

如果您已建立模組，請檢查下列問題：

- 模組是否已啟用？

  ```bash
  bin/magento module --enable Your_Module
  ```

  檢查 `app/etc/config.php` 新模組的檔案。

- 檢查檔案和目錄結構巢狀。 例如，配置檔案位於 `view/layout/` 目錄，而非 `view/frontend/layout` 目錄？ 範本是否在 `view/frontend/template` 目錄，而非 `view/frontend/templates` 目錄？

## 疑難排解：半分割

如果通常的疑犯沒有提供問題的解決方案，最快速的繼續方法是將問題分割成一半（或二分）。 透過此方法，您會排除大區塊，並分割剩餘的部分，以找出根本原因，而非以線性方式瀏覽程式碼。

請參閱下列圖表：

![二分圖表](../../../assets/playbooks/bisect.png)

![二分圖表](../../../assets/playbooks/bisect2.png)

雖然有數種等分方法，但Adobe建議依照此順序進行：

- 按主題二分
- 由認可二等分
- 按檔案平分

### 步驟1：依主題對等

如果問題可能與程式碼無關，請先消除大區塊。 要考慮的一些大型區塊包括：

- **Adobe Commerce框架** — 問題是否與Adobe Commerce有關，還是與其他連線系統有關？
- **伺服器和使用者端** — 清除瀏覽器快取和儲存空間。 問題已解決嗎？ 這可能會排除與伺服器相關的原因。 問題是否仍然存在？ 不需再浪費時間進行瀏覽器偵錯。
- **工作階段** — 問題是否發生在每個使用者身上？ 如果沒有，您的問題可能僅限於工作階段或瀏覽器相關主題。
- **快取** — 停用所有快取會變更任何專案嗎？ 若是如此，您可以專注於快取相關主題。
- **資料庫** — 問題是否發生在每個執行相同程式碼的環境上？ 如果沒有，請尋找組態中的問題以及其他資料庫相關主題。
- **程式碼** — 如果上述任何一項都無法解決問題，請尋找程式碼問題。

### 步驟2：依認可二分

如果問題從現在到兩個月前開始，請將程式碼復原到兩個月前。 確認問題是否仍然存在。 請再往前一個月。 問題是否在那裡發生？ 如果沒有，請繼續兩週。 現在發生嗎？ 返回上一週。 還在嗎？ 回到四天。 在某個時候，您只剩下一項認可，該認可可能包含與問題相關的程式碼。 您的根本原因現在可能僅限於在該認可中編輯的檔案。

您可以使用認可來取代周和天。 例如，回覆100個認可、回覆50、回覆25、回覆12。

### 步驟3：依檔案對等

- 將Adobe Commerce除以檔案型別（核心與非核心）。 首先，停用所有客戶和市集模組。 問題是否仍然存在？ 這很可能是非核心問題。
- 再次啟用（大約）中一半的模組 `app/etc/config.php` 檔案。 請注意相依性。 最好一次啟用具有相同主題的模組叢集。 問題是否仍然存在？
- 啟用剩餘模組的四分之一。 問題是否仍然存在？ 停用一半的已啟用專案。 此方法可協助您將根本原因隔離至單一模組。

## 節省時間

除了疑難排解技巧之外，本節還提供一些一般規則，有助於在偵錯期間節省時間。

### 限制資料

考慮您是需要完整目錄還是所有存放區檢視來復寫問題。 您可以偵錯資料庫複製的索引問題，其中您在開始偵錯之前已移除目錄的95%。 此方法可在索引過程中節省相當多的時間。 建立具有減少的存放區計數和目錄的使用者端資料庫復本。 根據您偵錯的區域，這可能也適用於其他實體（例如客戶）。

### 要求更多資訊

有時，在所有程式碼和技術工作中忘記的一個簡單步驟是：要求更多資訊。 全熒幕擷取、影片、與識別問題者的視訊會議聊天、復寫步驟、關於有問題事件是否發生其他看似不重要的事情的問題。 詢問某人預期會發生什麼事。 這真的是一個錯誤，還是只是對程式碼運作方式的誤解？

### 語言和口譯

問題的描述是否清楚？ 您確定沒有任何辭彙或說明可以透過多種方式解譯。 如果是這樣的話，請確定您談論的是相同的事情。

### 網際網路搜尋

使用與問題相關的詞匯進行網際網路搜尋。 其他人可能已經遇到相同問題的機率。 搜尋 [Adobe Commerce GitHub問題](https://github.com/magento/magento2/issues).

### 休息一下

如果問題解決時間過長，要找到解決方案會很困難。 放下工作，選擇其他工作或散步。 當您暫時忘記問題時，可能會找到答案。

## 工具

n98 magerun CLI工具([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2))提供從命令列使用Adobe Commerce的實用功能。 尤其是下列指令：

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## 程式碼片段

下列主題提供的程式碼片段可用於記錄或識別Commerce專案中的問題。

### 檢查商務是否使用XML檔案

在XML檔案中新增明顯的語法錯誤，以檢視它是否被使用。 開啟標籤，請勿針對例項關閉標籤：

```xml
<?xml version="1.0"?>
<test
```

若使用此檔案，則會產生錯誤。 如果沒有，您的模組可能無法使用或未針對例項啟用，或XML檔案可能位於錯誤的位置。

### 記錄

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB 獨白]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### 低層級記錄

在任何PHP檔案中始終可用的兩個範例：

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

對於棧疊追蹤：

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
