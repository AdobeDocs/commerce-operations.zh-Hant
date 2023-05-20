---
title: 配置自定義cron作業和cron組（教程）
description: 使用此逐步教程可建立自定義cron作業。
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# 配置自定義cron作業

本逐步教程介紹如何在示例模組中建立自定義cron作業和（可選）cron組。 您可以使用已擁有的模組，也可以使用我們的 [`magento2-samples` 儲存庫][samples]。

運行cron作業將導致將一行添加到 `cron_schedule` 表格中包含cron作業的名稱， `custom_cron`。

我們還將向您顯示如何選擇建立cron組，您可以使用該組運行自定義cron作業，其設定不是Commerce應用程式預設值。

在本教程中，我們假定：

- Commerce應用程式安裝在 `/var/www/html/magento2`
- 您的Commerce資料庫用戶名和密碼都 `magento`
- 執行所有操作時 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)

## 步驟1:獲取示例模組

要設定自定義cron作業，需要一個示例模組。 我們建議 `magento-module-minimal` 中。

如果您已經有了示例模組，則可以使用它；跳過此步驟和下一步，繼續執行步驟3:建立要運行cron的類。

**獲取示例模組**:

1. 將Commerce伺服器作為或切換到 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。
1. 更改為不在Commerce應用程式根目錄（例如，主目錄）中的目錄。
1. 克隆 [`magento2-samples` 儲存庫][samples]。

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   如果命令失敗並出現錯誤 `Permission denied (publickey).`，必須 [將SSH公鑰添加到GitHub.com][git-ssh]。

1. 建立要將示例代碼複製到的目錄：

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 複製示例模組代碼：

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 驗證複製的檔案是否正確：

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   您應看到以下結果：

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. 更新Commerce資料庫和架構：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

## 步驟2:驗證示例模組

在繼續之前，請驗證示例模組是否已註冊並啟用。

1. 運行以下命令：

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 確保模組已啟用。

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>如果輸出指示 `Module does not exist`查看 [步驟1](#step-1-get-a-sample-module) 小心點。 確保代碼位於正確的目錄中。 拼寫和大小寫很重要；如果有任何不同，則不載入模組。 還有，別忘了跑 `magento setup:upgrade`。

## 第3步：建立要運行cron的類

此步驟顯示一個用於建立cron作業的簡單類。 類只向 `cron_schedule` 確認已成功設定的表。

要建立類：

1. 為類建立目錄並更改到該目錄：

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 已建立名為 `Test.php` 目錄中的以下內容：

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## 第4步：建立 `crontab.xml`

的 `crontab.xml` 檔案設定運行自定義cron代碼的計畫。

建立 `crontab.xml` 如下 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 目錄：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

前面 `crontab.xml` 運行 `Magento/SampleMinimal/Cron/Test.php` 類每分鐘一次，導致行被添加到 `cron_schedule` 的子菜單。

要使cron計畫可以從管理員配置，請使用系統配置欄位的配置路徑。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

哪裡， `system/config/path` 是中定義的系統配置路徑 `etc/adminhtml/system.xml` 的下界。

## 第5步：編譯和快取清除

使用以下命令編譯代碼：

```bash
bin/magento setup:di:compile
```

然後使用以下命令清除快取：

```bash
bin/magento cache:clean
```

## 步驟6:驗證cron作業

此步驟說明如何使用上的SQL查詢成功驗證自定義cron作業 `cron_schedule` 資料庫表。

要驗證cron:

1. 運行Commerce cron作業：

   ```bash
   bin/magento cron:run
   ```

1. 輸入 `magento cron:run` 命令。

   第一次輸入命令時，它會對作業排隊；隨後，運行cron作業。 必須輸入命令 _至少_ 兩次。

1. 運行SQL查詢 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 如下：

   1. 輸入 `mysql -u magento -p`
   1. 在 `mysql>` 提示，輸入 `use magento;`
   1. 輸入 `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      結果應與以下內容類似：

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. （可選）驗證消息是否寫入Commerce的系統日誌：

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   您應看到以下一個或多個條目：

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   這些消息來自 `execute` 方法 `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

如果SQL命令和系統日誌不包含任何條目，請運行 `magento cron:run` 再命令幾次，然後等待。 資料庫更新可能需要一些時間。

## 步驟7（可選）:設定自定義克隆組

此步驟說明如何根據需要設定自定義克隆組。 如果希望自定義cron作業以不同於其他cron作業的計畫運行（通常為每分鐘一次），或者希望使用不同設定運行多個自定義cron作業，則應設定自定義cron組。

要設定自定義克隆組：

1. 開啟 `crontab.xml` 的子菜單。
1. 更改 `<group id="default">` 至 `<group id="custom_crongroup">`
1. 退出文本編輯器。
1. 建立 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` 內容如下：

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

有關選項含義的說明，請參見 [自定義crons引用](custom-cron-reference.md)。

## 第8步：驗證您的自定義克隆組

此 _可選_ 步驟顯示如何使用Admin驗證自定義cron組。

要驗證自定義克隆組：

1. 為自定義組運行Commerce cron作業：

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   至少運行兩次命令。

1. 清除快取：

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 以管理員身份登錄到管理員。
1. 按一下 **商店** > **設定** > **配置** > **高級** > **系統**。
1. 在右窗格中，展開 **克龍**。

   您的cron組顯示如下：

   ![您的自定義Cron組](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
