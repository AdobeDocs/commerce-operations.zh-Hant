---
title: 設定啟動程式引數的值
description: 瞭解如何設定Commerce應用程式的啟動程式引數。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 1%

---

# Bootstrap引數

本主題示範如何設定Commerce應用程式啟動程式引數的值。 請參閱[應用程式初始化和啟動載入概述](initialization.md)。

下表討論您可以設定的啟動程式引數：

| Bootstrap引數 | 說明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 指定自訂目錄和URL路徑 |
| MAGE_PROFILER | 啟用相依性圖表和HTML設定檔分析 |

>[!INFO]
>
>- 並非所有啟動程式引數都記錄下來。
>- 您現在使用[`magento deploy:mode:set {mode}`](../cli/set-mode.md)命令設定應用程式模式（開發人員、預設、生產）。

## 使用環境變數設定引數

本節將討論如何使用環境變數來設定啟動程式引數的值。

### 設定應用程式模式

您可以將啟動程式變數指定為系統範圍的環境變數，讓所有程式都能夠使用這些變數。

例如，您可以使用`MAGE_PROFILER`系統環境變數來指定模式，如下所示：

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用殼層特定的命令設定變數。 因為殼層有不同的語法，請查閱參考資料，例如[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)。

CentOS的Bash shell範例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>若在您設定效能評測器值後，瀏覽器中顯示`PHP Fatal error`，請重新啟動網頁伺服器。 原因可能與PHP位元碼快取有關，它會快取位元碼和PHP類別路徑。

## 設定Apache或Nginx的引數

本節探討如何指定Apache或Nginx的模式。

### Nginx設定

檢視[GitHub](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16)上的&#x200B;_Nginx範例組態_。

### Apache .htaccess設定

設定應用程式模式的一個方法是編輯`.htaccess`。 如此一來，您就不必變更Apache設定。

您可以修改下列任一位置的`.htaccess`，視您進入Commerce應用程式的入口點而定：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**設定變數**：

1. 在文字編輯器中開啟任何先前的檔案，並新增或取消註解所要的設定。

   例如，若要指定[模式](application-modes.md)，請取消註解下列專案：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 將`MAGE_PROFILER`的值設定為下列任一值：

   ```
   firebug
   csvfile
   <custom value>
   ```

1. 將變更儲存至`.htaccess`；您不需要重新啟動Apache即可讓變更生效。

### Apache設定

Apache Web Server支援使用`mod_env`指令設定應用程式模式。

在`mod_env`Apache版本2.2[和](https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv)Apache版本2.4[中，Apache ](https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv)指示詞稍有不同。

下列程式說明如何在Apache虛擬主機中設定應用程式模式。 這不是使用`mod_env`指示詞的唯一方法；如需詳細資訊，請參閱Apache檔案。

>[!TIP]
>
>下節假設您已設定虛擬主機。 如果沒有，請查閱資源，例如[此DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)。

**若要為Ubuntu上的Apache指定啟動程式變數**：

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟您的虛擬主機設定檔。

   例如，如果您的虛擬主機名為`my.magento`，

   - Apache 2.4： `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2： `vim /etc/apache2/sites-available/my.magento`

1. 在虛擬主機組態中的任何位置，新增下列行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存變更並退出文字編輯器。
1. 啟用虛擬主機（如果尚未啟用）：

   ```bash
   a2ensite <virtual host config file name>
   ```

   例如，

   ```bash
   a2ensite my.magento.conf
   ```

1. 設定模式後，請重新啟動網頁伺服器：

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

>[!TIP]
>
>本節假設您已設定虛擬主機。 如果沒有，請查閱資源，例如[此DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6)。

**若要為CentOS上的Apache指定啟動程式變數**：

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟`/etc/httpd/conf/httpd.conf`。

1. 在虛擬主機組態中的任何位置，新增下列行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存變更並退出文字編輯器。

1. 設定模式後，請重新啟動網頁伺服器：

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

