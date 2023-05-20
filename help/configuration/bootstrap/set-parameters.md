---
title: 設定引導參數的值
description: 瞭解如何為Commerce應用程式設定引導參數。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Bootstrap參數

本主題演示如何設定Commerce應用程式引導參數的值。 請參閱 [應用程式初始化和引導概述](initialization.md)。

下表討論了可設定的引導參數：

| Bootstrap參數 | 說明 |
| ------------------- | -------------------------------------------- |
| 影像(_D) | 指定自定義目錄和URL路徑 |
| MAGE_PROFILER | 啟用依賴關係圖和HTML分析 |

>[!INFO]
>
>- 並非所有引導參數都記錄在案。
>- 現在，使用 [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 的子菜單。


## 使用環境變數設定參數

本節討論如何使用環境變數設定引導參數的值。

### 設定應用程式模式

可以將引導變數指定為系統範圍的環境變數，這樣所有進程都可以使用它們。

例如，您可以使用 `MAGE_PROFILER` 系統環境變數，指定如下模式：

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用殼特定命令設定變數。 由於shell的語法不同，因此請參考引用，如 [unix.stackexchange.com][unix-stackx]。

Bash Shell示例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>如果 `PHP Fatal error` 在設定探查器值後在瀏覽器中顯示，重新啟動Web伺服器。 原因可能與PHP位元組代碼快取有關，該快取快取快取位元組代碼和PHP類空間。

## 設定Apache或Nginx的參數

本節討論如何指定Apache或Nginx的模式。

### Nginx設定

查看 [Nginx示例配置] 上 _GitHub_。

### Apache .htaccess設定

設定應用程式模式的一種方法是編輯 `.htaccess`。 這樣，您就不必更改Apache設定。

可以修改 `.htaccess` 在以下任何位置，具體取決於您指向Commerce應用程式的入口點：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**設定變數**:

1. 在文本編輯器中開啟前面的任何檔案，然後添加或取消注釋所需的設定。

   例如，要指定 [模式](application-modes.md)，取消注釋：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 設定 `MAGE_PROFILER` 下列任一項：

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 將更改保存到 `.htaccess`;您不需要重新啟動Apache，更改才能生效。

### Apache設定

Apache Web伺服器支援使用 `mod_env` 指令。

阿帕奇 `mod_env` 指令在 [Apache 2.2版] 和 [Apache 2.4版]。

下面的過程說明如何在Apache虛擬主機中設定應用程式模式。 這不是唯一的使用方法 `mod_env` 指令；有關詳細資訊，請參閱Apache文檔。

>[!TIP]
>
>以下部分假定您已經設定了虛擬主機。 如果沒有，請參考資源，如 [本DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)。

**為Ubuntu上的Apache指定引導變數**:

1. 作為用戶 `root` 權限，在文本編輯器中開啟虛擬主機配置檔案。

   例如，如果虛擬主機被命名 `my.magento`。

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. 在虛擬主機配置中的任何位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   比如說，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 保存更改並退出文本編輯器。
1. 如果尚未啟用虛擬主機，請執行以下操作：

   ```bash
   a2ensite <virtual host config file name>
   ```

   比如說，

   ```bash
   a2ensite my.magento.conf
   ```

1. 設定模式後，重新啟動Web伺服器：

   - 烏班圖： `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>本節假定您已經設定了虛擬主機。 如果沒有，請參考資源，如 [本DigitalOcean教程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6)。

**為CentOS上的Apache指定引導變數**:

1. 作為用戶 `root` 權限，開啟 `/etc/httpd/conf/httpd.conf` 的子菜單。

1. 在虛擬主機配置中的任何位置，添加以下行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   比如說，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 保存更改並退出文本編輯器。

1. 設定模式後，重新啟動Web伺服器：

   - 烏班圖： `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache 2.2版]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache 2.4版]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx示例配置]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
