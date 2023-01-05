---
title: 設定引導參數的值
description: 了解如何為商務應用程式設定引導程式參數。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Bootstrap參數

本主題演示如何設定Commerce應用程式引導參數的值。 請參閱 [應用程式初始化和引導概述](initialization.md).

下表討論了可設定的引導參數：

| Bootstrap參數 | 說明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 指定自訂目錄和URL路徑 |
| MAGE_PROFILER | 啟用相依性圖表和HTML分析 |

>[!INFO]
>
>- 並非所有引導參數都記錄在案。
>- 您現在可以使用 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 命令。


## 使用環境變數設定參數

本節討論如何使用環境變數設定引導參數的值。

### 設定應用程式模式

您可以將引導變數指定為系統範圍的環境變數，以便所有進程都能使用這些變數。

例如，您可以使用 `MAGE_PROFILER` 系統環境變數來指定模式，如下所示：

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用殼特定命令設定變數。 由於殼的語法不同，因此請查詢引用，如 [unix.stackexchange.com][unix-stackx].

CentOS的Bash殼層範例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>若 `PHP Fatal error` 在設定探查器值後，在瀏覽器中顯示，請重新啟動Web伺服器。 原因可能與PHP位元組碼快取有關，這些快取位元組碼和PHP類路徑。

## 設定Apache或Nginx的參數

本節探討如何指定Apache或Nginx的模式。

### Nginx設定

請參閱 [Nginx設定範例] on _GitHub_.

### Apache .htaccess設定

設定應用程式模式的一種方式是編輯 `.htaccess`. 如此一來，您便不需要變更Apache設定。

您可以修改 `.htaccess` （視您進入商務應用程式的入口點而定）位於下列任一位置：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**若要設定變數**:

1. 在文字編輯器中開啟任何先前的檔案，然後新增或取消對所需設定的註解。

   例如，若要指定 [模式](application-modes.md)，取消下列內容的註解：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 設定 `MAGE_PROFILER` 至下列任一項目：

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 將變更儲存至 `.htaccess`;您不需要重新啟動Apache，變更才會生效。

### Apache設定

Apache Web伺服器支援使用 `mod_env` 指令。

Apache `mod_env` 指令在 [Apache 2.2版] 和 [Apache 2.4版].

以下過程說明如何在Apache虛擬主機中設定應用程式模式。 這並非唯一的使用方法 `mod_env` 指令；如需詳細資訊，請參閱Apache檔案。

>[!TIP]
>
>以下章節假設您已設定虛擬主機。 若尚未這麼做，請諮詢資源，例如 [本DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**為Ubuntu上的Apache指定引導變數**:

1. 身為使用者 `root` 權限，請在文本編輯器中開啟虛擬主機配置檔案。

   例如，如果您的虛擬主機名為 `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 在虛擬主機配置中的任何位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存您的變更並退出文字編輯器。
1. 如果尚未啟用虛擬主機，請啟用此選項：

   ```bash
   a2ensite <virtual host config file name>
   ```

   例如，

   ```bash
   a2ensite my.magento.conf
   ```

1. 設定模式後，重新啟動Web伺服器：

   - 烏本圖： `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>本節假設您已設定虛擬主機。 若尚未這麼做，請諮詢資源，例如 [本DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**為CentOS上的Apache指定引導變數**:

1. 身為使用者 `root` 權限，開啟 `/etc/httpd/conf/httpd.conf` 在文字編輯器中。

1. 在虛擬主機配置中的任何位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存您的變更並退出文字編輯器。

1. 設定模式後，重新啟動Web伺服器：

   - 烏本圖： `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache 2.2版]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache 2.4版]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx設定範例]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
