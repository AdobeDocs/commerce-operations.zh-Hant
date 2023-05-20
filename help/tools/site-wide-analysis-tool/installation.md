---
title: 安裝指南
description: 使用本指南進行安裝 [!DNL Site-Wide Analysis Tool] 您的網站
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# 安裝指南

的 [!DNL Site-Wide Analysis Tool] 提供全天候即時效能監控、報告和建議，以確保Adobe Commerce在雲基礎架構安裝方面的安全性和可操作性。 它還提供有關可用和已安裝的修補程式、第三方擴展以及您的Adobe Commerce安裝的詳細資訊。

>[!INFO]
>
>學習 [如何啟用](../site-wide-analysis-tool/access.md) 這樣 [!DNL Site-Wide Analysis Tool] 並生成報告。

如果您在本地安裝了Adobe Commerce，請在基礎架構上安裝代理以使用該工具。 您無需在Adobe Commerce的雲基礎架構項目上安裝代理。

## 代理

的 [!DNL Site-Wide Analysis Tool] 代理允許您使用 [!DNL Site-Wide Analysis Tool] 為Adobe Commerce提供內部設施。

的 [!DNL Site-Wide Analysis Tool] Agent收集應用程式和業務資料，對其進行分析，並提供有關安裝運行狀況的更多見解，以便您能夠改善客戶體驗。 它可監控您的應用程式，並幫助您確定效能、安全性、可用性和應用程式問題。

安裝代理需要執行以下步驟：

1. 驗證系統要求。

1. 在 [!UICONTROL Commerce Services Connector] 擴展。

1. 安裝代理。

1. 運行代理。

>[!INFO]
>
>代理支援多節點Adobe Commerce安裝。 在每個節點上安裝和配置代理。

## 系統要求

安裝代理之前，您的內部基礎架構必須滿足以下要求：

- 作業系統

   - [!DNL Linux x86-64] 分佈，如 [!DNL Red Hat® Enterprise Linux (RHEL)]。 [!DNL CentOS]。 [!DNL Ubuntu]。 [!DNL Debian]，類似
   >[!IMPORTANT]
   >
   >Adobe Commerce不支援 [!DNL Microsoft Windows] 或 [!DNL macOS]。

- Adobe Commerce2.4.1或更高版本

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell實用程式

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

代理需要 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 擴展安裝在系統上， [配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) API密鑰。 要驗證擴展是否已安裝，請運行以下命令：

```bash
bin/magento module:status Magento_ServicesId
```

如果已安裝擴展並使用其他服務的現有API密鑰進行配置，則 **必須重新生成API密鑰** 並在Adobe Commerce管理員中更新代理。

1. 將您的網站放入 [維護模式](../../installation/tutorials/maintenance-mode.md)。

1. 登錄 [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)。

   >[!NOTE]
   >
   > 如果訪問帳戶時遇到問題，請參閱 [無法登錄Adobe Commerce支援或雲帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 中。

1. 按一下 **[!UICONTROL API Portal]**。

1. 按一下 **[!UICONTROL Delete]** 現有API密鑰旁邊。

1. [配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 新的API密鑰。

>[!IMPORTANT]
>
> 如果在API門戶中生成新密鑰，請立即更新 [!DNL Admin configuration]。 如果生成新密鑰，但不更新 [!DNL Admin]，您的SaaS擴展將不再工作，您將丟失寶貴的資料。

如果未安裝擴展，請使用以下說明安裝它：

1. 將擴展添加到 `composer.json` 檔案並安裝。

   ```bash
   composer require magento/services-id
   ```

1. 啟用擴展。

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. 更新資料庫架構。

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取。

   ```bash
   bin/magento cache:clean
   ```

1. [配置API密鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 將擴展連接到系統。

## 安裝代理

我們建立了 [shell指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 以簡化安裝。 我們建議使用shell指令碼，但您可以 [手動安裝](#manual) 的雙曲餘切值。

>[!INFO]
>
>安裝代理後，當有新版本可用時，代理將自動更新。

### 指令碼

1. 下載並執行shell指令碼。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >建議在根Adobe Commerce項目目錄外安裝代理。

1. 驗證安裝。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下載和安裝代理後， [配置它以運行](#run-the-agent) 使用以下方法之一：

   - [服務](#service) （如果您具有根訪問權限，則首選）

   - [克龍](#cron)

### 手動 {#manual}

如果你不想用我們 [shell指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 要安裝代理，必須按照以下步驟手動安裝代理：

1. 建立要下載代理的目錄。

   >[!TIP]
   >
   >建議在根Adobe Commerce項目目錄外安裝代理。

1. 下載二進位檔案並解壓縮。

   >[!INFO]
   >
   >使用 [!DNL Site-Wide Analysis Tool]，您必須首先閱讀並接受從Adobe Commerce管理員訪問儀表板時顯示的使用條款。

   對於 **AMD64** 體系結構：

   1. 下載啟動程式存檔。

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 解壓縮啟動程式存檔。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   對於 **ARM64** 體系結構：

   1. 下載啟動程式存檔。

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 解壓縮啟動程式存檔。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *（可選）* 驗證校驗和檔案的簽名。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（可選）* 驗證校驗和。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 建立 `config.yaml` 檔案。

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. 驗證安裝。

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下載和安裝代理後，必須 [配置它以運行](#run-the-agent) 使用以下方法之一：

   - [服務](#service) （如果您具有根訪問權限，則首選）

   - [克龍](#cron)

## 運行代理 {#run-the-agent}

建議將代理配置為作為服務運行。 如果您對基礎架構的訪問權限有限，並且沒有根權限，則必須使用 [克隆](#cron) 的雙曲餘切值。

### 服務 {#service}

1. 建立系統設備檔案 `(/etc/systemd/system/scheduler.service)` 使用以下配置(替換 `<filesystemowner>` 擁有安裝代理和Adobe Commerce軟體的目錄的UNIX®用戶)。 如果以根用戶身份下載代理，請更改目錄和嵌套檔案所有者。

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. 啟動服務。

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. 驗證服務是否已啟動並正在運行。

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### 克龍 {#cron}

如果您沒有根權限或沒有將服務配置為根的權限，則可以改用cron。

更新您的cron計畫：

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 卸載

運行以下命令從系統卸載服務並刪除所有生成的檔案：

1. 停止計畫程式。

   ```bash
   systemctl stop scheduler
   ```

1. 禁用計畫程式。

   ```bash
   systemctl disable scheduler
   ```

1. 刪除計畫程式服務 `systemd` 設備檔案。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新載入 `systemd` 管理器配置。

   ```bash
   systemctl daemon-reload
   ```

1. 重置任何 `systemd` 單位來自失敗狀態。

   ```bash
   systemctl reset-failed
   ```

1. 刪除計畫程式服務目錄。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 刪除調度程式二進位檔案。

   ```bash
   rm /usr/local/bin/scheduler
   ```

如果已將代理配置為使用cron運行，請使用以下說明：

1. 從crontab清單中刪除代理。

   ```bash
   crontab -e
   ```

1. 停止正在運行的作業。

   ```bash
   ps aux | grep scheduler
   ```

1. 刪除安裝代理的目錄。

   ```bash
   rm -rf swat-agent
   ```

## 故障排除

### 未正確分析訪問密鑰

如果未正確分析訪問密鑰，您可能會看到以下錯誤：

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.swat.magento.com/linux-amd64.json: 403 Forbidden
```

要解決此錯誤，請嘗試以下步驟：

1. 執行 [指令碼安裝](#scripted)，保存輸出，並查看輸出是否有錯誤。
1. 查看生成的 `config.yaml` 並驗證Commerce實例和PHP的路徑是否正確。
1. 確保運行調度程式的用戶位於 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md) Unix組或與檔案系統所有者是同一用戶。
1. 確保 [Commerce Services連接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 已正確安裝密鑰，並嘗試更新密鑰以將擴展連接到系統。
1. [卸載](#uninstall) 更新密鑰並使用 [安裝指令碼](#scripted)。
1. 運行計畫程式並查看是否仍收到相同的錯誤。
1. 如果仍然收到相同的錯誤，請在 `config.yaml` 調試並開啟支援票證。


>[!INFO]
>
>請參閱 [如何訪問 [!DNL Site-Wide Analysis Tool] 生成報告](../site-wide-analysis-tool/access.md)。
