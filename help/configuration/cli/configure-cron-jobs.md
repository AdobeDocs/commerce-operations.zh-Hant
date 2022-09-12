---
title: 配置並運行cron作業
description: 了解如何管理cron作業。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---


# 設定cron作業

{{file-system-owner}}

若干商務功能至少需要一個cron工作，以排程未來的活動。 以下是這些活動的部分清單：

- 目錄價格規則
- 電子報
- 產生Google網站地圖
- 客戶警報/通知（產品價格變動，產品退回現貨）
- 重新索引
- 私人銷售(僅限Adobe Commerce)
- 貨幣匯率的自動更新
- 所有商務電子郵件（包括訂單確認和交易）

>[!WARNING]
>
>您無法再執行 `dev/tools/cron.sh` 因為已移除指令碼。

>[!INFO]
>
>商務取決於許多重要系統功能（包括索引）的正確cron作業配置。 若未正確設定，表示商務將無法如預期般運作。

UNIX系統將任務安排給特定用戶執行，使用 _crontab_，此檔案包含對cron守護程式的說明，該守護程式告知該守護程式生效，即「在此日期此時運行此命令」。 每個用戶都有自己的crontab，任何給定crontab中的命令都以擁有它的用戶身份執行。

若要在網頁瀏覽器中執行cron，請參閱 [保護cron.php在瀏覽器中執行](../security/secure-cron-php.md).

## 建立或移除Commerce crontab

本節探討如何建立或移除您的Commerce crontab（即Commerce cron作業的設定）。

此 _crontab_ 是用來執行cron作業的設定。

商務應用程式使用可搭配不同設定執行的cron任務。 PHP命令列配置控制重新索引器、生成電子郵件、生成Sitemap等的常規cron作業。

>[!WARNING]
>
>- 為避免在安裝和升級期間出現問題，我們強烈建議您將相同的PHP設定應用於PHP命令行配置和PHP Web伺服器插件的配置。 如需詳細資訊，請參閱 [必需的PHP設定](../../installation/prerequisites/php-settings.md).
>- 在多節點系統中， crontab只能在一個節點上運行。 只有當您出於與效能或可擴充性相關的原因而設定多個Web節點時，才適用此方法。


### 建立商務crontab

從2.2版開始，Commerce會為您建立crontab。 我們將Commerce crontab添加到Commerce檔案系統所有者的任何配置的crontab中。 換言之，如果您已為其他擴充功能或應用程式設定crontab，我們會將Commerce crontab新增至它。

Commerce crontab位於內 `#~ MAGENTO START` 和 `#~ MAGENTO END` crontab中的注釋。

要建立Commerce crontab:

1. 以登入或切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用 `--force` 重寫現有crontab。

>[!INFO]
>
>- `magento cron:install` 不會重寫內現有的crontab `#~ MAGENTO START` 和 `#~ MAGENTO END` crontab中的注釋。
>- `magento cron:install --force` 對商務評論以外的任何cron工作沒有影響。


要查看crontab，請輸入以下命令作為檔案系統所有者：

```bash
crontab -l
```

範例如下：

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>此 `update/cron.php` 檔案已在Commerce 2.4.0中移除，如果此檔案存在於您的安裝中，則可安全地移除。
>
>任何 `update/cron.php` 和 `bin/magento setup:cron:run` 也應從crontab的

### 刪除Commerce crontab

只有在卸載Commerce應用程式之前，才應刪除Commerce crontab。

要刪除Commerce crontab，請執行以下操作：

1. 以登入，或切換至 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到Commerce安裝目錄。
1. 輸入以下命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>此命令對外部的cron作業沒有影響 `#~ MAGENTO START` 和 `#~ MAGENTO END` crontab中的注釋。

## 從命令列執行cron

命令選項：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

where `--group` 指定要執行的cron群組（忽略此選項以為所有群組執行cron）

要運行索引cron作業，請輸入：

```bash
bin/magento cron:run --group index
```

要運行預設cron作業，請輸入：

```bash
bin/magento cron:run --group default
```

若要設定自訂cron作業和群組，請參閱 [設定自訂cron作業和cron群組](../cron/custom-cron.md).

>[!INFO]
>
>您必須執行兩次cron:第一次發現要運行的任務，第二次發現要運行的任務。 第二次cron執行必須發生在 `scheduled_at` 每個任務的時間。

## 記錄

全部 `cron` 作業資訊已從 `system.log` 進入 `cron.log`.
依預設，可在下列位置找到cron資訊： `<install_directory>/var/log/cron.log`.
所有cron作業的例外都由記錄者 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

除了登入 `cron.log`:

- 失敗的作業 `ERROR` 和 `MISSED` 狀態會記錄到 `<install_directory>/var/log/support_report.log`.

- 具有 `ERROR` 狀態一律記錄為 `CRITICAL` in `<install_directory>/var/log/exception.log`.

- 具有 `MISSED` 狀態記錄為 `INFO` 在 `<install_directory>/var/log/debug.log` 目錄（僅限開發人員模式）。

>[!INFO]
>
>所有cron資料也會寫入 `cron_schedule` 表。 表格提供cron作業的歷史記錄，包括：
>
>- 作業ID和程式碼
>- 狀態
>- 建立日期
>- 排程日期
>- 執行日期
>- 完成日期
>
>要查看表中的記錄，請登錄命令行上的Commerce資料庫，然後輸入 `SELECT * from cron_schedule;`.
