---
title: 可選軟體
description: 瞭解有關可安裝支援Adobe Commerce和Magento Open Source內部安裝的可選軟體的更多資訊。
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# 可選軟體

我們強烈建議您安裝NTP以確保與cron相關的任務正常執行。 （例如，伺服器日期可能是過去或將來。）

本主題中討論的其它可選實用程式可能會幫助您進行安裝；但是，它們無需安裝或使用Adobe Commerce或Magento Open Source。

## 安裝和配置網路時間協定(NTP)

[NTP](https://www.ntp.org/) 使伺服器能夠使用 [全局可用池伺服器](https://www.ntppool.org/en/)。 我們建議您使用您信任的NTP伺服器，無論這些伺服器是內部網路的專用硬體解決方案還是外部公共伺服器。

如果您正在多台主機上部署Adobe Commerce或Magento Open Source，則NTP是一種簡單的方法，可確保它們的時鐘全部同步，而不管伺服器位於什麼時區。 此外，與cron相關的任務（如索引和事務性電子郵件）取決於伺服器時鐘是否準確。

### 在Ubuntu上安裝和配置NTP

輸入以下命令以安裝NTP:

```bash
apt-get install ntp
```

繼續 [使用NTP池伺服器](#use-ntp-pool-servers)。

### 在CentOS上安裝和配置NTP

安裝和配置NTP:

1. 輸入以下命令以查找相應的NTP軟體：

   ```bash
   yum search ntp
   ```

1. 選擇要安裝的包。 比如說， `ntp.x86_64`。

1. 安裝軟體包。

   ```bash
   yum -y install ntp.x86_64
   ```

1. 輸入以下命令，以便在伺服器啟動時啟動NTP。

   ```bash
   chkconfig ntpd on
   ```

1. 繼續下一節。

### 使用NTP池伺服器

選擇池伺服器取決於您。 如果使用NTP池伺服器，則ntp.org建議您使用 [池伺服器](https://www.ntppool.org/en/) 與伺服器的時區相近，如 [「NTP池項目」頁](https://www.ntppool.org/en/use.html)。 如果部署中所有主機都可使用專用NTP伺服器，則可以改用該伺服器。

1. 開啟 `/etc/ntp.conf` 的子菜單。

1. 查找類似以下行：

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 替換這些行或添加指定NTP池伺服器或其他NTP伺服器的其他行。 最好指定多個。

1. 以下是使用三台基於美國的NTP伺服器的示例：

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 將更改保存到 `/etc/ntp.conf` 並退出文本編輯器。

1. 重新啟動服務。

   * 烏班圖： `service ntp restart`

   * CentOS: `service ntpd restart`

1. 輸入 `date` 來檢查伺服器的日期。

   如果日期不正確，請確保在防火牆中開啟NTP客戶端埠（通常為UDP 123）。

   嘗試 `ntpdate _[pool server hostname]_` 的子菜單。 如果失敗，請搜索它返回的錯誤。

   如果所有其他操作都失敗，請嘗試重新啟動伺服器。

## 建立phpinfo.php

的 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 檔案顯示大量有關PHP及其副檔名的資訊。

>[!NOTE]
>
>使用 `phpinfo.php` 在開發系統中 _僅_。 這可能是生產中的安全問題。

在Web伺服器的任意位置添加以下代碼：

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

有關詳細資訊，請參見 [phinfo手冊頁](https://www.php.net/manual/en/function.phpinfo.php)。

要查看結果，請在瀏覽器的位置或地址欄位中輸入以下URL:

```http
http://<web server host or IP>/phpinfo.php
```

如果顯示404（未找到）錯誤，請檢查以下內容：

* 如有必要，啟動Web伺服器。
* 確保防火牆允許埠80上的通信。

   [幫助烏班圖](https://help.ubuntu.com/community/UFW)

   [CentOS幫助](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

phpMyAdmin應用程式是一個易於使用且免費的資料庫管理實用程式。 您可以使用它檢查和處理資料庫的內容。 您必須以MySQL資料庫管理用戶身份登錄到phpMyAdmin。

有關phpMyAdmin的詳細資訊，請參見 [phpMyAdmin首頁](https://www.phpmyadmin.net/)。

有關安裝的詳細資訊，請參見 [phpMyAdmin安裝文檔](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install)。

>[!NOTE]
>
>在開發系統中使用phpMyAdmin _僅_。 這可能是生產中的安全問題。

1. 要使用phpMyAdmin，請在瀏覽器的地址或位置欄位中輸入以下命令：

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 出現提示時，使用MySQL資料庫登錄 `root` 或管理用戶的用戶名和密碼。
