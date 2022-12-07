---
title: 安裝指南
description: '"使用本指南安裝 [!DNL Site-Wide Analysis Tool] 」'
source-git-commit: 5603d0feee6ec9dd5e8b534a0e64df274d7ab84d
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# 安裝指南

此 [!DNL Site-Wide Analysis Tool] 提供24/7即時效能監控、報告和建議，以確保Adobe Commerce在雲端基礎架構安裝上的安全性和可操作性。 它還提供有關可用和已安裝的修補程式、第三方擴展和Adobe Commerce安裝的詳細資訊。

>[!INFO]
>
>學習 [如何啟用](../site-wide-analysis-tool/access.md) the [!DNL Site-Wide Analysis Tool] 和產生報表。

如果您有本地安裝的Adobe Commerce，請在您的基礎架構上安裝代理，以使用此工具。 您不需要在雲端基礎架構專案的Adobe Commerce上安裝代理程式。

## 代理

此 [!DNL Site-Wide Analysis Tool] 代理允許您使用 [!DNL Site-Wide Analysis Tool] 為Adobe Commerce的內部安裝。

此 [!DNL Site-Wide Analysis Tool] 代理收集應用程式和業務資料，對其進行分析，並提供有關安裝運行狀況的其他分析，以便您能夠改進客戶體驗。 它可監控您的應用程式，並幫助您識別效能、安全性、可用性和應用程式問題。

安裝代理程式需要下列步驟：

1. 驗證系統要求。

1. 在 [!UICONTROL Commerce Services Connector] 擴充功能。

1. 安裝代理。

1. 運行代理。

>[!INFO]
>
>代理支援多節點Adobe Commerce安裝。 在每個節點上安裝並配置代理。

## 系統需求

安裝代理之前，您的本地基礎架構必須滿足以下要求：

- 作業系統

   - [!DNL Linux x86-64] 分佈，如 [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]，和類似
   >[!IMPORTANT]
   >
   >Adobe Commerce不支援 [!DNL Microsoft Windows] 或 [!DNL macOS].

- Adobe Commerce 2.4.1或更新版本

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

代理程式需要 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 擴充功能，將安裝在您的系統上， [已配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 使用API金鑰。 若要確認已安裝擴充功能，請執行下列命令：

```bash
bin/magento module:status Magento_ServicesConnector
```

如果您已安裝擴充功能，並使用不同服務的現有API金鑰進行設定，則您 **必須重新產生API金鑰** 並在Adobe Commerce管理員中更新代理程式。

1. 將您的網站放入 [維護模式](../../installation/tutorials/maintenance-mode.md).

1. 登入 [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > 如果您在存取帳戶時遇到問題，請參閱 [無法登入Adobe Commerce支援或雲端帳戶](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 疑難排解說明。

1. 按一下 **[!UICONTROL API Portal]**.

1. 按一下 **[!UICONTROL Delete]** 在現有API金鑰旁。

1. [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 新的API金鑰。

>[!IMPORTANT]
>
> 若您在API入口網站中產生新金鑰，請立即更新 [!DNL Admin configuration]. 如果您產生新金鑰，且不更新 [!DNL Admin]，您的SaaS擴展將無法繼續運作，您將丟失寶貴的資料。

如果未安裝擴充功能，請依照下列指示進行安裝：

1. 將擴充功能新增至 `composer.json` 檔案並安裝。

   ```bash
   composer require magento/services-connector:1.*
   ```

1. 啟用擴充功能。

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. 更新資料庫架構。

   ```bash
   bin/magento setup:upgrade
   ```

1. [設定API金鑰](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 將擴充功能連線至您的系統。

## 安裝代理

我們已建立 [殼層指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 簡化安裝。 建議您使用shell指令碼，但您可以遵循 [手動安裝](#manual) 方法（如有必要）。

>[!INFO]
>
>安裝代理後，當有新版本可用時，代理將自行更新。

### 指令碼

1. 下載並執行shell指令碼。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >建議您在根Adobe Commerce專案目錄之外安裝代理程式。

1. 驗證安裝。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下載並安裝代理後， [設定它以執行](#run-the-agent) 使用下列其中一種方法：

   - [服務](#service) （如果您有根存取權，則建議使用）

   - [Cron](#cron)

### 手動 {#manual}

如果您不想使用 [殼層指令碼](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 要安裝代理，則必須按照以下步驟手動安裝：

1. 建立要下載代理的目錄。

   >[!TIP]
   >
   >建議您在根Adobe Commerce專案目錄之外安裝代理程式。

1. 下載二進位檔案並將其解壓縮。

   >[!INFO]
   >
   >若要使用 [!DNL Site-Wide Analysis Tool]，您必須先閱讀並接受從Adobe Commerce管理員存取控制面板時顯示的使用條款。

   若 **AMD64** 架構：

   1. 下載啟動器存檔。

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 拆開啟動器存檔的包裝。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   若 **ARM64** 架構：

   1. 下載啟動器存檔。

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 拆開啟動器存檔的包裝。

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

1. 建立 `config.yaml` 檔案中包含下列內容。

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

1. 下載和安裝代理後，您必須 [設定它以執行](#run-the-agent) 使用下列其中一種方法：

   - [服務](#service) （如果您有根存取權，則建議使用）

   - [Cron](#cron)

## 運行代理 {#run-the-agent}

建議將代理設定為以服務形式運行。 如果您對基礎架構的存取權限有限，且沒有根權限，則必須使用 [cron](#cron) 。

### 服務 {#service}

1. 建立系統單元檔案 `(/etc/systemd/system/scheduler.service)` (取代 `<filesystemowner>` 擁有安裝代理和Adobe Commerce軟體的目錄的UNIX®用戶)。 如果以超級用戶身份下載代理，請更改目錄和嵌套檔案所有者。

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

### Cron {#cron}

如果您沒有根權限或沒有將服務設定為根的權限，則可以改用cron。

更新您的cron排程：

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 解除安裝

運行以下命令以從系統卸載服務並刪除所有生成的檔案：

1. 停止排程器。

   ```bash
   systemctl stop scheduler
   ```

1. 停用排程器。

   ```bash
   systemctl disable scheduler
   ```

1. 移除排程器服務的 `systemd` 單位檔案。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新載入 `systemd` 管理器配置。

   ```bash
   systemctl daemon-reload
   ```

1. 重設任何 `systemd` 單位數。

   ```bash
   systemctl reset-failed
   ```

1. 刪除調度程式服務目錄。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 移除排程器二進位檔案。

   ```bash
   rm /usr/local/bin/scheduler
   ```

如果您已將代理設定為使用cron運行，請使用以下說明：

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

## 覆寫設定檔案

您可以使用環境變數來覆寫安裝期間在設定檔案中指定的值。 這樣可保留與舊版代理的回溯相容性。 如需建議的值，請參閱下表：

| 屬性 | 說明 |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | 安裝代理程式時提供的公司或站點名稱 |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | PHP CLI解釋器的路徑(通常 `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | 安裝Adobe Commerce應用程式的根目錄(通常 `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Adobe Commerce安裝的資料庫使用者 |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | 為Adobe Commerce安裝指定用戶的資料庫密碼 |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Adobe Commerce安裝的資料庫主機 |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Adobe Commerce安裝的資料庫名稱 |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Adobe Commerce安裝的資料庫埠(通常 `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Adobe Commerce安裝的表格首碼(預設值： `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | 您的Adobe Commerce安裝是否有次要資料庫實例(通常 `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | 代理的臨時目錄(通常 `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | 收集第一次執行的資料(通常 `1`) |
| `SWAT_AGENT_LOG_LEVEL` | 根據嚴重性(通常為 `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | 啟用自動升級(升級後需要重新啟動；如果禁用了選項，代理不檢查升級； `true` 或 `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | 啟用沙箱模式以在測試環境中使用代理 |

>[!INFO]
>
>請參閱 [如何存取 [!DNL Site-Wide Analysis Tool] 產生報表](../site-wide-analysis-tool/access.md).
