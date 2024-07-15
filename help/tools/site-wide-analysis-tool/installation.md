---
title: 安裝指南
description: 使用本指南為您的網站安裝 [!DNL Site-Wide Analysis Tool]
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: f72316b3baee52ef6b000afa281a2e146f560ead
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# 安裝指南

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce內部部署客戶將停止使用[!DNL Site-Wide Analysis Tool]。

[!DNL Site-Wide Analysis Tool]提供24小時全年無休的即時效能監控、報告和建議，以確保Adobe Commerce在雲端基礎結構安裝上的安全性和可操作性。 此外，也提供可用和已安裝修補程式、協力廠商擴充功能及Adobe Commerce安裝的詳細資訊。

>[!INFO]
>
>瞭解[如何啟用](../site-wide-analysis-tool/access.md) [!DNL Site-Wide Analysis Tool]並產生報表。

如果您有內部部署的Adobe Commerce，請在您的基礎結構上安裝代理程式以使用此工具。 您不需要在雲端基礎結構專案上安裝Adobe Commerce代理程式。

## 代理程式

[!DNL Site-Wide Analysis Tool]代理程式可讓您將[!DNL Site-Wide Analysis Tool]用於Adobe Commerce的內部部署。

[!DNL Site-Wide Analysis Tool]代理程式會收集應用程式和業務資料、分析這些資料，並提供關於您安裝狀況的其他深入分析，以便您改善客戶體驗。 它可以監視您的應用程式，並協助您識別效能、安全性、可用性以及應用程式問題。

安裝代理程式需要下列步驟：

1. 驗證系統需求。

1. 在[!UICONTROL Commerce Services Connector]擴充功能中設定API金鑰。

1. 安裝代理程式

1. 執行代理程式

>[!INFO]
>
>代理程式支援多節點Adobe Commerce安裝。 在每個節點上安裝及設定代理程式。

## 系統需求

安裝代理程式之前，您的內部部署基礎結構必須符合下列需求：

- 作業系統

   - [!DNL Linux x86-64]分配，例如[!DNL Red Hat® Enterprise Linux (RHEL)]、[!DNL CentOS]、[!DNL Ubuntu]、[!DNL Debian]等

  >[!IMPORTANT]
  >
  >[!DNL Microsoft Windows]或[!DNL macOS]不支援Adobe Commerce。

- Adobe Commerce 2.4.5-p1或更新版本（因為依賴Service Connector）

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/殼層公用程式

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

代理程式需要將[[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)擴充功能安裝在您的系統上，並使用API金鑰[設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)。 若要驗證是否已安裝擴充功能，請執行以下命令：

```bash
bin/magento module:status Magento_ServicesId
```

如果您已安裝擴充功能，並使用其他服務的現有API金鑰進行設定，則&#x200B;**必須重新產生API金鑰**，並在代理程式的Adobe Commerce管理程式中加以更新。

1. 將您的網站置於[維護模式](../../installation/tutorials/maintenance-mode.md)。

1. 登入[account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)。

   >[!NOTE]
   >
   > 如果您無法存取帳戶，請參閱[無法登入Adobe Commerce支援或雲端帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)以取得疑難排解說明。

1. 按一下&#x200B;**[!UICONTROL API Portal]**。

1. 按一下現有API金鑰旁的&#x200B;**[!UICONTROL Delete]**。

1. [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)新的API金鑰。

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

1. [設定API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)，將擴充功能連線至您的系統。

## 安裝代理程式

我們已建立[殼層指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)以簡化安裝。 我們建議您使用Shell指令碼，但您可以視需要遵循[手動安裝](#manual)方法。

>[!INFO]
>
>安裝代理程式後，當有新版本可用時，它會自行更新。

### 指令碼

1. 下載並執行殼層指令碼。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >我們建議您在根Adobe Commerce專案目錄外部安裝代理程式。

1. 驗證安裝。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下載並安裝代理程式之後，[使用下列其中一種方法設定它執行](#run-the-agent)：

   - [服務](#service) （如果您有根存取許可權，則偏好使用）

   - [Cron](#cron)

### 手動 {#manual}

如果您不想使用我們的[殼層指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)來安裝代理程式，則必須依照下列步驟手動安裝：

1. 建立您要下載代理程式的目錄。

   >[!TIP]
   >
   >我們建議您在根Adobe Commerce專案目錄外部安裝代理程式。

1. 下載二進位檔案並將其解壓縮。

   >[!INFO]
   >
   >若要使用[!DNL Site-Wide Analysis Tool]，您必須先閱讀並接受您從Adobe Commerce管理員存取儀表板時顯示的使用條款。

   針對&#x200B;**AMD64**&#x200B;架構：

   1. 下載啟動器封存。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 將啟動器封存解壓縮。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   針對&#x200B;**ARM64**&#x200B;架構：

   1. 下載啟動器封存。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 將啟動器封存解壓縮。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *（選擇性）*&#x200B;驗證總和檢查碼的簽章。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（選擇性）*&#x200B;驗證總和檢查碼。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 建立包含以下內容的`config.yaml`檔案。

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

## 執行代理程式 {#run-the-agent}

我們建議將代理程式設定為以服務方式執行。 如果您對基礎結構的存取權有限，且沒有根許可權，則必須改用[cron](#cron)。

### 服務 {#service}

1. 使用下列組態建立系統單位檔案`(/etc/systemd/system/scheduler.service)` (將`<filesystemowner>`取代為擁有安裝代理程式和Adobe Commerce軟體之目錄的UNIX®使用者)。 如果您以root使用者身份下載代理程式，請變更目錄和巢狀檔案擁有者。

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

1. 驗證服務是否已啟動且執行中。

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

如果您沒有root許可權或沒有將服務設定為root的許可權，則可以改用cron。

更新您的cron排程：

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 解除安裝

執行以下命令，從您的系統解除安裝服務，並移除所有產生的檔案：

1. 停止排程器。

   ```bash
   systemctl stop scheduler
   ```

1. 停用排程器。

   ```bash
   systemctl disable scheduler
   ```

1. 移除排程器服務的`systemd`單位檔案。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新載入`systemd`管理員組態。

   ```bash
   systemctl daemon-reload
   ```

1. 從失敗狀態重設任何`systemd`個裝置。

   ```bash
   systemctl reset-failed
   ```

1. 移除排程器服務目錄。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 移除排程器二進位檔案。

   ```bash
   rm /usr/local/bin/scheduler
   ```

如果您將代理程式設定為使用cron執行，請使用下列指示：

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

### 存取金鑰未正確剖析

如果您的存取金鑰未正確剖析，您可能會看到以下錯誤：

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

若要解決此錯誤，請嘗試下列步驟：

1. 執行[指令碼安裝](#scripted)，儲存輸出，並檢閱輸出是否有錯誤。
1. 檢閱產生的`config.yaml`檔案，並確認您的Commerce執行個體和PHP的路徑是否正確。
1. 確定執行排程器的使用者位於[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md) Unix群組中，或是與檔案系統擁有者相同的使用者。
1. 請確定[Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)金鑰已正確安裝，並嘗試更新金鑰以將擴充功能連線至您的系統。
1. [在更新金鑰後解除安裝](#uninstall)代理程式，並使用[安裝指令碼](#scripted)重新安裝。
1. 執行排程器，檢視您是否仍收到相同的錯誤。
1. 如果您仍收到相同的錯誤，請增加`config.yaml`中的記錄層級以偵錯並開啟支援票證。

### *SIGFAULT*&#x200B;錯誤

如果您在執行二進位檔時看到&#x200B;*SIGFAULT*錯誤，您可能不會以Adobe Commerce和Agent檔案的檔案擁有者的身分執行此動作。
若要解決問題，請檢查代理程式目錄中所有與Adobe Commerce檔案擁有者具有相同使用者，以及二進位檔案的檔案，是否也應該在該使用者下執行。
您可以使用`chown`命令來變更檔案擁有者並切換到適當的使用者。
請確定您的模組化機制（Cron或System.d）在適當的使用者下執行流程。

>[!INFO]
>
>請參閱[如何存取 [!DNL Site-Wide Analysis Tool] 並產生報表](../site-wide-analysis-tool/access.md)。
