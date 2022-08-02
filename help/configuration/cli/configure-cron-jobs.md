---
title: 配置並運行cron作業
description: 瞭解如何管理cron作業。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# 配置cron作業

{{file-system-owner}}

幾個Commerce功能至少需要一個cron作業，該作業會安排將來的活動。 以下是這些活動的部分清單：

- 目錄價格規則
- 通訊
- 生成Google小集
- 客戶警報/通知（產品價格變動，產品退回庫存）
- 重新索引
- 私人銷售(僅Adobe Commerce)
- 貨幣匯率的自動更新
- 所有Commerce電子郵件（包括訂單確認和事務處理）

>[!WARNING]
>
>你不能再 `dev/tools/cron.sh` 因為指令碼已被刪除。

>[!INFO]
>
>商務需要對許多重要的系統功能（包括索引）進行適當的cron作業配置。 未能正確設定它意味著Commerce將無法按預期運行。

UNIX系統計畫由特定用戶使用 _crontab_，該檔案包含對cron守護進程的說明，這些說明告訴該守護進程在此日期的此時運行此命令。 每個用戶都有其自己的crontab ，並且任何給定crontab中的命令都作為擁有它的用戶執行。

要在Web瀏覽器中運行cron，請參見 [在瀏覽器中運行的安全cron.php](../security/secure-cron-php.md)。

## 建立或刪除Commerce crontab

本節討論如何建立或刪除Commerce crontab（即Commerce cron作業的配置）。

的 _crontab_ 是用於運行cron作業的配置。

Commerce應用程式使用可以使用不同配置運行的cron任務。 PHP命令行配置控制重新索引索引器、生成電子郵件、生成站點地圖等的常規cron作業。

>[!WARNING]
>
>- 為避免在安裝和升級過程中出現問題，強烈建議您對PHP命令行配置和PHP Web伺服器插件的配置都應用相同的PHP設定。 有關詳細資訊，請參見 [所需的PHP設定](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html)。
>- 在多節點系統中，crontab只能在一個節點上運行。 僅當出於與效能或可擴充性相關的原因設定了多個Web節點時，這才適用於您。


### 建立Commerce crontab

從2.2版開始，Commerce會為您建立一個crontab。 我們將Commerce crontab添加到Commerce檔案系統所有者的任何已配置crontab中。 換句話說，如果您已經為其他擴展或應用程式設定了crontab ，我們會將Commerce crontab添加到其中。

Commerce crontab位於內部 `#~ MAGENTO START` 和 `#~ MAGENTO END` 在crontab中輸入注釋。

要建立Commerce crontab:

1. 作為或切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用 `--force` 重寫現有的crontab。

>[!INFO]
>
>- `magento cron:install` 不重寫內部現有crontab `#~ MAGENTO START` 和 `#~ MAGENTO END` 在crontab中輸入注釋。
>- `magento cron:install --force` 對Commerce評論之外的任何cron作業沒有影響。


要查看crontab ，請輸入以下命令作為檔案系統所有者：

```bash
crontab -l
```

示例如下：

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>的 `update/cron.php` 檔案已在Commerce 2.4.0中刪除，如果此檔案在您的安裝中存在，則可以安全地刪除該檔案。
>
>任何引用 `update/cron.php` 和 `bin/magento setup:cron:run` 也應從crontab中刪除

### 刪除Commerce crontab

您應僅在卸載Commerce應用程式之前刪除Commerce crontab。

要刪除Commerce crontab :

1. 登錄身份或切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 更改為Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>此命令對外部的cron作業沒有影響 `#~ MAGENTO START` 和 `#~ MAGENTO END` 在crontab中輸入注釋。

## 從命令行運行cron

命令選項：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

何處 `--group` 指定要運行的cron組（省略此選項以為所有組運行cron）

要運行索引cron作業，請輸入：

```bash
bin/magento cron:run --group index
```

要運行預設cron作業，請輸入：

```bash
bin/magento cron:run --group default
```

要設定自定義cron作業和組，請參閱 [配置自定義cron作業和cron組](../cron/custom-cron.md)。

>[!INFO]
>
>必須運行兩次cron:第一次發現要運行的任務，第二次發現要運行的任務。 第二個cron運行必須發生在 `scheduled_at` 每項任務的時間。

## 記錄

全部 `cron` 作業資訊已從 `system.log` 分隔 `cron.log`。
預設情況下，cron資訊可在 `<install_directory>/var/log/cron.log`。
cron作業中的所有異常都由 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`。

除了登錄 `cron.log`:

- 失敗的作業 `ERROR` 和 `MISSED` 狀態記錄到 `<install_directory>/var/log/support_report.log`。

- 與 `ERROR` 狀態始終記錄為 `CRITICAL` 在 `<install_directory>/var/log/exception.log`。

- 與 `MISSED` 狀態記錄為 `INFO` 的 `<install_directory>/var/log/debug.log` 目錄（僅限開發人員模式）。

>[!INFO]
>
>所有cron資料也寫入 `cron_schedule` 的下界。 該表提供了cron作業的歷史記錄，包括：
>
>- 作業ID和代碼
>- 狀態
>- 建立日期
>- 計畫日期
>- 執行日期
>- 完成日期
>
>要查看表中的記錄，請登錄到命令行上的Commerce資料庫，然後輸入 `SELECT * from cron_schedule;`。
