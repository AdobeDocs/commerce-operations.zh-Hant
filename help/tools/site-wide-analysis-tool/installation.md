---
title: 安裝指南
description: '使用此指南安裝您的網站 [!DNL Site-Wide Analysis Tool] '
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# 安裝指南

>[!IMPORTANT]
>
>自 2024 年 4 月 23 日起， [!DNL Site-Wide Analysis Tool] 將對所有 Adobe Systems Commerce 本地客戶停用。

提供 [!DNL Site-Wide Analysis Tool] 24/7 全天候即時性能監控、報告和建議，以確保 Adobe Systems Commerce 在雲端基礎結構安裝上的安全性和可作性。 它還提供了有關可用和已安裝的修補程序、協力廠商擴展以及 Adobe Systems Commerce 安裝的詳細資訊。

>[!INFO]
>
>瞭解如何 [啟用](../site-wide-analysis-tool/access.md) [!DNL Site-Wide Analysis Tool] 和產生報表。

如果您有內部部署的Adobe Commerce，請在您的基礎結構上安裝代理程式以使用此工具。 您不需要在雲端基礎結構專案上安裝Adobe Commerce代理程式。

## 代理程式

[!DNL Site-Wide Analysis Tool]代理程式可讓您將[!DNL Site-Wide Analysis Tool]用於Adobe Commerce的內部部署。

[!DNL Site-Wide Analysis Tool]代理程式會收集應用程式和業務資料、分析這些資料，並提供關於您安裝狀況的其他深入分析，以便您改善客戶體驗。 它可以監視您的應用程式，並協助您識別效能、安全性、可用性以及應用程式問題。

安裝代理需要執行以下步驟：

1. 驗證系統要求。

1. 在擴充功能中 [!UICONTROL Commerce Services Connector] 設定 API 金鑰。

1. 安裝代理。

1. 運行代理。

>[!INFO]
>
>此代理支持多節點Adobe Systems商務安裝。 在每個節點上安裝和配置代理。

## 系統需求

在安裝代理之前，本地基礎結構必須滿足以下要求：

- 操作系統

   - [!DNL Linux x86-64]分佈，例如 [!DNL Red Hat® Enterprise Linux (RHEL)]、[!DNL CentOS]、 [!DNL Ubuntu][!DNL Debian]和類似

  >[!IMPORTANT]
  >
  >Adobe Systems 或 [!DNL macOS]不支持[!DNL Microsoft Windows]商務。

- Adobe Systems Commerce 2.4.5-p1 或更高版本（由於服務連接器的依賴關係）

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell 公用程式

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

代理要求 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 在系統上安裝擴展並使用 [API 金鑰進行配置](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 。 若要驗證是否已安裝擴展，請執行以下命令：

```bash
bin/magento module:status Magento_ServicesId
```

如果您已安裝擴展並使用其他服務的現有 API 金鑰對其進行配置， **則必須重新生成 API 金鑰** 並在代理的Adobe Systems商務管理中更新它。

1. 將您的網站置於 [維護模式](../../installation/tutorials/maintenance-mode.md)。

1. 登入 [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)。

   >[!NOTE]
   >
   > 如果您在訪問帳戶時遇到問題，請参閱 [無法登錄 Adobe Systems Commerce 支持或雲端帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 以獲取故障排除説明。

1. 按兩下 **[!UICONTROL API Portal]**。

1. 按兩下 **[!UICONTROL Delete]** 現有 API 金鑰旁邊的按鈕。

1. [設定](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 新的 API 金鑰。

>[!IMPORTANT]
>
> 如果您在API入口網站產生新金鑰，請立即更新[!DNL Admin configuration]中的API金鑰。 如果您產生新的金鑰但未更新[!DNL Admin]中的金鑰，您的SaaS擴充功能將無法再運作，而且您會遺失重要的資料。

如果未安裝擴充功能，請依照下列指示進行安裝：

1. 將擴充功能新增至您的`composer.json`檔案並加以安裝。

   ```bash
   composer require magento/services-id
   ```

1. 啟用擴充功能。

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. 更新資料庫結構。

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取。

   ```bash
   bin/magento cache:clean
   ```

1. [配置 API 金鑰](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 以將擴展連接到系統。

## 安裝代理

我們創建了一個 [shell 腳本](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 來簡化安裝。 我們建議使用shell腳本，但如有必要，您可以追隨 [手動安裝](#manual) 方法。

>[!INFO]
>
>安裝代理后，它將在有新版本可用時自行更新。

### 腳本

1. 下載並執行shell腳本。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >建議在根 Adobe Systems Commerce 專案目錄之外安裝代理。

1. 驗證安裝。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下載並安裝代理後， [將其配置為使用以下方法之一運行](#run-the-agent) ：

   - [服務](#service) （如果您有根存取許可權，則偏好使用）

   - [Cron](#cron)

### 手動 {#manual}

如果您不想使用我們的[殼層指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)來安裝代理程式，則必須依照下列步驟手動安裝：

1. 建立您要下載代理程式的目錄。

   >[!TIP]
   >
   >我們建議您在根Adobe Commerce專案目錄外部安裝代理程式。

1. 下載二進位檔並將其解壓縮。

   >[!INFO]
   >
   >[!DNL Site-Wide Analysis Tool]要使用 ，您必須首先閱讀並接受從Adobe Systems商務管理員訪問儀錶板時顯示的使用條款。

   針對&#x200B;**AMD64**&#x200B;架構：

   1. 下載啟動器封存。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 將啟動器封存解壓縮。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   **對於 ARM64** 架構：

   1. 下載 啟動器 封存。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 解壓縮啟動器封存。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *（可選）* 驗證校驗和文件的簽名。

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

1. `config.yaml`建立包含以下內容的檔。

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

1. 下載及安裝代理程式之後，您必須[使用下列其中一種方法，將其設定為執行](#run-the-agent)：

   - [服務](#service) （如果您有根存取許可權，則偏好使用）

   - [Cron](#cron)

## 運行代理 {#run-the-agent}

建議將代理配置為作為服務運行。 如果您對基礎架構的訪問許可權有限且沒有 root 許可權，則必須改用 [cron](#cron) 。

### 服務 {#service}

1. 建立具有以下配置的 systemd 單元文件 `(/etc/systemd/system/scheduler.service)` （替換為 `<filesystemowner>` 擁有安裝代理和 Adobe Systems Commerce 軟體的目錄的 UNIX® 用戶）。 如果將代理下載為根用戶，請將目錄和嵌套檔擁有者。

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

1. Launch服務。

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

### Cron {#cron}

如果您沒有根許可權或沒有將服務配置為根的許可權，則可以改用cron。

更新您的cron計劃：

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 卸載

執行以下命令以從系統中卸載服務並刪除所有產生的檔案：

1. 停止排程器。

   ```bash
   systemctl stop scheduler
   ```

1. 停用排程器。

   ```bash
   systemctl disable scheduler
   ```

1. 拿掉排程器服務的 `systemd` 單元檔。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新載入 `systemd` 管理員配置。

   ```bash
   systemctl daemon-reload
   ```

1. `systemd`重設處於故障狀態的任何设备。

   ```bash
   systemctl reset-failed
   ```

1. 拿掉排程器服務目錄。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 拿掉排程器二進位檔。

   ```bash
   rm /usr/local/bin/scheduler
   ```

如果將代理配置為改為使用cron運行，請使用以下說明：

1. 從crontab清單中移除代理程式。

   ```bash
   crontab -e
   ```

1. 停止執行中的工作。

   ```bash
   ps aux | grep scheduler
   ```

1. 移除安裝代理程式的目錄。

   ```bash
   rm -rf swat-agent
   ```

## 疑難排解

### 存取金鑰未正確解析

如果未正確解析存取金鑰，您可能會看到以下錯誤：

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

若要解決此錯誤，請嘗試以下步驟：

1. [執行文稿安裝](#scripted)，保存輸出，並查看輸出是否存在錯誤。
1. 檢查生成的 `config.yaml` 文件，並驗證 Commerce 執行個體 和 PHP 的路徑是否正確。
1. 確保運行排程器的用戶位於文件系統擁有者[&#128279;](../../installation/prerequisites/file-system/overview.md) Unix 群組 中，或者與文件系統擁有者用戶相同。
1. 確保 [正確安裝了商務服務連接器](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) 密鑰，並嘗試更新它們以將擴展連接到系統。
1. [更新金鑰后卸載](#uninstall)代理，然後使用安裝腳本[&#128279;](#scripted)重新安裝。
1. 運行排程器，看看是否仍然收到相同的錯誤。
1. 如果仍然收到相同的錯誤，請提高 to `config.yaml` 偵錯 中的日誌級別並打開支援票證。

### *SIGFAULT* 錯誤

如果在運行二進位檔時看到 *SIGFAULT* 錯誤，則可能不會將其作為Adobe Systems商務和代理檔的檔擁有者運行。若要解決此問題，請檢查代理目錄中與Adobe Systems Commerce 檔具有的檔擁有者具有相同用戶的所有文件，並且二進位檔是否也應在該用戶下運行。您可以使用該 `chown` 命令更改文件擁有者並切換到相應的用戶。確保您的守護進程機制（Cron 或 System.d）在適當的用戶下運行進程。

>[!INFO]
>
>請參閱 [如何訪問 [!DNL Site-Wide Analysis Tool] 和生成報告](../site-wide-analysis-tool/access.md)。
