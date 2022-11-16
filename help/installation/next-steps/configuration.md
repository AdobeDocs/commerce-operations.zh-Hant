---
title: 配置應用程式
description: 了解Adobe Commerce和Magento Open Source內部部署所需的安裝後設定。
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---


# 配置應用程式

現在您已完成Adobe Commerce或Magento Open Source的安裝，需要加以設定。 本主題提供一些建議的配置設定。

## 設定cron

UNIX任務調度程式cron對應用程式的日常操作至關重要。 它會排程重新索引、電子報、電子郵件和網站地圖等項目。 A *crontab* 是cron設定。

您必須在 *crontab*，或某些核心功能（和某些協力廠商擴充功能）無法正常運作。

有關cron的詳細資訊，包括如何從命令行刪除crontab和運行cron，請參見 [設定並執行cron](../../configuration/cli/configure-cron-jobs.md).

## 安全設定與建議

安裝後，我們建議使用下列項目：

* 請確定檔案所有權和權限已正確設定
* 強烈建議 [更改預設管理URI](../tutorials/admin-uri.md) 從 `admin` 別的
* 請確定 [`X-Frame-Option` HTTP標題](../../configuration/security/xframe-options.md) 已正確設定。
* 防止跨網站指令碼(XSS)，方法為 [保護模板](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

如果安裝者 [複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)，請務必在部署應用程式時，僅包含生產環境所需的檔案和資料夾。 不需要的檔案和資料夾可能會暴露安全風險。

## 啟用Apache伺服器重寫

如果使用Apache Web伺服器，則必須啟用伺服器重寫才能正確顯示頁面。 否則，您會看到沒有樣式和其他問題的頁面。

[Apache伺服器重寫的區段](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 多Web節點環境中的快取

如果您有多個Web節點，則 *不能* 使用應用程式的預設檔案快取，因為Web節點之間沒有同步。 換言之，一個Web節點上的活動僅寫入該Web節點的檔案系統。 後續活動（如果在其他Web節點上執行）可能導致寫入不必要的檔案，或可能導致錯誤。

請改用 [雷迪斯](../../configuration/cache/config-redis.md) 預設值 [快取](https://glossary.magento.com/cache) 和頁面快取。

## 伺服器設定

本節簡要討論我們建議您針對應用程式運行所在的伺服器考慮的設定。 其中有些設定與應用程式無直接關係；這些僅提供建議。

### 日誌旋轉

UNIX `logrotate` 應用工具允許您管理生成大量日誌檔案的系統。 它允許自動輪換、壓縮、刪除和郵寄日誌檔案。 每個日誌檔案都可以每天、每週、每月處理，或者當日誌檔案超過指定大小時。

如需詳細資訊，請參閱下列其中一項：

* [操作方法：最終的log rotate命令教程，包含10個示例](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [堆棧交換](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 手冊頁](https://linuxconfig.org/logrotate-8-manual-page)

### 設定Iptables規則以使各種服務能夠通信

無論您有一台或多台伺服器，都必須在防火牆中開啟埠，以便使服務能夠通信。 例如，如果您將Solr搜尋引擎與Adobe Commerce搭配使用，則必須啟用它以與Web伺服器通訊。 如果您有多個Web節點，則必須允許它們彼此通信。

更多資訊：

* 烏本圖： [Ubuntu檔案頁面](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS作法](https://wiki.centos.org/HowTos/Network/IPTables).

### 安全增強Linux(SELinux)規則

我們沒有建議您是否使用SELinux;但是，如果確實使用了它，則必須將服務配置為與配置iptables類似地彼此通信。

更多資訊：

* 烏本圖： [德比安手冊](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux)

### 設定電子郵件伺服器

Adobe Commerce和Magento Open Source需要電子郵件伺服器。 我們不建議使用特定伺服器，但您可以嘗試下列任一操作：

* CentOS的Postfix([數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS檔案](https://www.centos.org))
* Ubuntu的Postfix([數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu檔案](https://help.ubuntu.com/community/MailServer))

### 精簡搜尋引擎以提升效能：

自2.4.0起，所有安裝都需要Elasticsearch或OpenSearch。

* [安裝及設定搜尋引擎](../../configuration/search/overview-search.md)

### 設定訊息佇列

自2.3.0版起，Adobe Commerce和Magento Open Source包含訊息佇列功能。 在舊版中，僅適用於Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 僅限Adobe Commerce的設定

只有在使用Adobe Commerce時，才可設定下列項目：

* [分割資料庫以用於檢出、訂單管理和其他資料庫表](../../configuration/storage/multi-master.md)
