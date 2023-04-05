---
title: 可選軟體
description: 進一步了解您可安裝哪些可選軟體以支援Adobe Commerce和Magento Open Source的內部部署安裝。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 可選軟體

強烈建議您安裝NTP以確保與cron相關的任務正常執行。 （例如，伺服器日期可能是過去或未來。）

本主題中討論的其他可選實用程式可能會幫助您安裝；不過，安裝或使用Adobe Commerce或Magento Open Source並不需要這些參數。

## 安裝和配置網路時間協定(NTP)

[NTP](https://www.ntp.org/) 使伺服器能夠使用 [全局可用池伺服器](https://www.ntppool.org/en/). 建議您使用您信任的NTP伺服器，無論這些伺服器是您的內部網路或外部公共伺服器的專用硬體解決方案。

如果要在多台主機上部署Adobe Commerce或Magento Open Source，則NTP是一種簡單的方法，可以保證其時鐘都同步，無論伺服器處於哪個時區。 此外，與cron相關的任務（例如索引和交易式電子郵件）取決於伺服器時鐘是否準確。

### 在Ubuntu上安裝和配置NTP

輸入以下命令以安裝NTP:

```bash
apt-get install ntp
```

繼續 [使用NTP池伺服器](#use-ntp-pool-servers).

### 在CentOS上安裝和配置NTP

要安裝和配置NTP:

1. 輸入以下命令以查找相應的NTP軟體：

   ```bash
   yum search ntp
   ```

1. 選擇要安裝的包。 例如， `ntp.x86_64`.

1. 安裝套件。

   ```bash
   yum -y install ntp.x86_64
   ```

1. 輸入以下命令，以便在伺服器啟動時啟動NTP。

   ```bash
   chkconfig ntpd on
   ```

1. 繼續下一節。

### 使用NTP池伺服器

選擇池伺服器取決於您。 如果使用NTP池伺服器，則ntp.org建議您使用 [池伺服器](https://www.ntppool.org/en/) 接近您伺服器的時區，如 [「NTP池」項目頁](https://www.ntppool.org/en/use.html). 如果您有一個專用NTP伺服器，該伺服器可用於部署中的所有主機，則可以改用該伺服器。

1. 開啟 `/etc/ntp.conf` 在文字編輯器中。

1. 尋找類似下列的行：

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 替換這些行或添加指定NTP池伺服器或其他NTP伺服器的其他行。 多指定一個是好辦法。

1. 以下是使用三個基於美國的NTP伺服器的示例：

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 將變更儲存至 `/etc/ntp.conf` 並退出文字編輯器。

1. 重新啟動服務。

   * 烏本圖： `service ntp restart`

   * CentOS: `service ntpd restart`

1. 輸入 `date` 來檢查伺服器的日期。

   如果日期不正確，請確保在防火牆中開啟NTP客戶端埠（通常為UDP 123）。

   嘗試 `ntpdate _[pool server hostname]_` 命令。 如果失敗，請搜尋傳回的錯誤。

   如果其他所有操作都失敗，請嘗試重新啟動伺服器。

## 建立phpinfo.php

此 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 檔案顯示了有關PHP及其副檔名的大量資訊。

>[!NOTE]
>
>使用 `phpinfo.php` 在開發系統中 _僅限_. 這可能是生產環境中的安全問題。

將下列程式碼新增至Web伺服器資料夾中的任何位置：

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

如需詳細資訊，請參閱 [phpinfo手動頁面](https://www.php.net/manual/en/function.phpinfo.php).

若要檢視結果，請在瀏覽器的位置或位址欄位中輸入下列URL:

```http
http://<web server host or IP>/phpinfo.php
```

如果顯示404（找不到）錯誤，請檢查下列項目：

* 如有必要，請啟動Web伺服器。
* 確保防火牆允許埠80上的通信。

   [為烏邦圖提供幫助](https://help.ubuntu.com/community/UFW)

   [CentOS的說明](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

phpMyAdmin應用程式是一個易於使用的免費資料庫管理實用程式。 您可以使用它來檢查和操控資料庫的內容。 您必須以MySQL資料庫管理用戶身份登錄phpMyAdmin。

有關phpMyAdmin的詳細資訊，請參見 [phpMyAdmin首頁](https://www.phpmyadmin.net/).

有關安裝的詳細資訊，請參閱 [phpMyAdmin安裝檔案](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>在開發系統中使用phpMyAdmin _僅限_. 這可能是生產環境中的安全問題。

1. 要使用phpMyAdmin，請在瀏覽器的地址或位置欄位中輸入以下命令：

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 出現提示時，使用MySQL資料庫登錄 `root` 或管理用戶的用戶名和密碼。
