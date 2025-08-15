---
title: 設定並執行cron工作
description: 瞭解如何管理cron工作。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# 設定cron作業

{{file-system-owner}}

有幾個Commerce功能至少需要一個cron工作，這會安排未來發生活動。 這些活動的部分清單如下：

- 目錄價格規則
- 電子報
- 產生Google Sitemap
- 客戶警示/通知（產品價格變更、產品補貨）
- 重新索引
- 私人銷售(僅限Adobe Commerce)
- 自動更新貨幣匯率
- 所有Commerce電子郵件（包括訂單確認和異動）

>[!WARNING]
>
>您無法再執行`dev/tools/cron.sh`，因為指令碼已移除。

>[!INFO]
>
>Commerce仰賴許多重要系統功能的正確cron工作設定，包括編制索引。 若未正確設定，表示Commerce將無法如預期運作。

UNIX系統使用&#x200B;_crontab_&#x200B;排程由特定使用者執行的工作，這個檔案包含對cron協助程式的指示，指示協助程式在生效時「在此日期執行此命令」。 每個使用者都有自己的crontab，而且任何指定crontab中的命令都會以擁有該命令的使用者身分執行。

若要在網頁瀏覽器中執行cron，請參閱[在瀏覽器中執行的cron.php安全](../security/secure-cron-php.md)。

## 建立或移除Commerce crontab

本節探討如何建立或移除您的Commerce crontab (即Commerce cron作業的設定)。

_crontab_&#x200B;是用於執行cron工作的組態。

Commerce應用程式會使用能以不同設定執行的cron工作。 PHP命令列配置控制一般cron工作，該工作會重新索引索引器、產生電子郵件、產生Sitemap等等。

>[!WARNING]
>
>- 為避免在安裝和升級期間發生問題，我們強烈建議您將相同的PHP設定套用到PHP命令列配置和PHP Web伺服器外掛程式的配置。 如需詳細資訊，請參閱[必要的PHP設定](../../installation/prerequisites/php-settings.md)。
>- 在多節點系統中，crontab只能在一個節點上執行。 唯有因效能或擴充性相關原因而設定多個Webnode時，才能使用此功能。

### 建立Commerce crontab

從2.2版開始，Commerce會為您建立crontab。 我們會將Commerce crontab新增至Commerce檔案系統擁有者的任何已設定crontab。 換言之，如果您已針對其他擴充功能或應用程式設定crontab，我們會新增Commerce crontab至擴充功能或應用程式。

Commerce crontab位於您的crontab中的`#~ MAGENTO START`和`#~ MAGENTO END`個評論內。

若要建立Commerce crontab：

1. 登入為[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)，或切換為檔案系統擁有者。
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用`--force`重寫現有的crontab。

>[!INFO]
>
>- `magento cron:install`不會重寫您crontab中`#~ MAGENTO START`和`#~ MAGENTO END`個註解中的現有crontab。
>- `magento cron:install --force`對Commerce註解以外的任何cron工作沒有影響。

若要檢視crontab，請輸入下列命令作為檔案系統擁有者：

```bash
crontab -l
```

範例如下：

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>`update/cron.php`檔案已在Commerce 2.4.0中移除，若此檔案存在於您的安裝中，則可安全地移除它。
>
>對`update/cron.php`和`bin/magento setup:cron:run`的任何參考也應從crontab&#39;中移除

### 移除Commerce crontab

您應該先移除Commerce crontab，再解除安裝Commerce應用程式。

若要移除Commerce crontab：

1. 以或切換身分登入[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>這個命令對您crontab中`#~ MAGENTO START`和`#~ MAGENTO END`個註解以外的cron工作沒有影響。

## 從命令列執行cron

命令選項：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

其中`--group`指定要執行的cron群組（省略此選項即可對所有群組執行cron）

若要執行索引cron工作，請輸入：

```bash
bin/magento cron:run --group index
```

若要執行預設cron工作，請輸入：

```bash
bin/magento cron:run --group default
```

若要設定自訂cron作業和群組，請參閱[設定自訂cron作業和cron群組](../cron/custom-cron.md)。

>[!INFO]
>
>您必須執行兩次cron：第一次是探索要執行的工作，第二次是執行工作本身。 第二個cron執行必須發生在每個工作的`scheduled_at`時間或之後。

## 記錄

所有`cron`工作資訊已從`system.log`移至單獨的`cron.log`。
依預設，您可以在`<install_directory>/var/log/cron.log`找到cron資訊。
`\Magento\Cron\Observer\ProcessCronQueueObserver::execute`會記錄cron工作的所有例外狀況。

除了登入`cron.log`之外：

- 具有`ERROR`和`MISSED`狀態的失敗工作會記錄到`<install_directory>/var/log/support_report.log`。

- 在`ERROR`中，狀態為`CRITICAL`的工作一律記錄為`<install_directory>/var/log/exception.log`。

- 狀態為`MISSED`的工作會在`INFO`目錄中記錄為`<install_directory>/var/log/debug.log` （僅限開發人員模式）。

>[!INFO]
>
>所有cron資料也會寫入Commerce資料庫的`cron_schedule`資料表。 此表格提供cron工作的歷史記錄，包括：
>
>- 工作ID和代碼
>- 狀態
>- 建立日期
>- 排定日期
>- 執行日期
>- 完成日期
>
>若要檢視表格中的記錄，請在命令列上登入Commerce資料庫並輸入`SELECT * from cron_schedule;`。
