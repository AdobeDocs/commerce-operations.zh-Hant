---
title: 配置應用程式
description: 瞭解Adobe Commerce和Magento Open Source內部部署所需的安裝後配置。
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 配置應用程式

既然您已完成安裝Adobe Commerce或Magento Open Source，則需要配置它。 本主題提供了一些建議的配置設定。

## 設定cron

UNIX任務調度程式cron對應用程式的日常操作至關重要。 它會安排諸如重新編製索引、新聞通訊、電子郵件和小小集之類的活動。 A *crontab* 是cron配置。

必須在中安裝Adobe Commerce和Magento Open Source服務 *crontab*&#x200B;或某些核心功能（和某些第三方擴展）無法正常工作。

有關cron的詳細資訊，包括如何從命令行中刪除crontab並運行cron，請參見 [配置並運行cron](../../configuration/cli/configure-cron-jobs.md)。

## 安全設定和建議

安裝後，我們建議執行以下操作：

* 確保正確設定檔案所有權和權限
* 我們強烈建議 [更改預設的Admin URI](../tutorials/admin-uri.md) 從 `admin` 到別的
* 確保 [`X-Frame-Option` HTTP頭](../../configuration/security/xframe-options.md) 設定正確。
* 通過 [保護模板](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

如果安裝者 [克隆GitHub儲存庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)，確保在部署應用程式時，僅包含生產環境所需的檔案和資料夾。 不需要的檔案和資料夾可能會暴露安全風險。

## 啟用Apache伺服器重寫

如果使用Apache Web伺服器，則必須啟用伺服器重寫才能正確顯示頁面。 否則，您會看到沒有樣式和其他問題的頁面。

[有關Apache伺服器重寫的部分](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 在多Web節點環境中的快取

如果有多個Web節點， *不能* 使用應用程式的預設檔案快取，因為web節點之間沒有同步。 換句話說，一個Web節點上的活動僅寫入該Web節點的檔案系統。 如果在另一個Web節點上執行後續活動，則可能導致寫入不必要的檔案或導致錯誤。

而是使用 [雷迪斯](../../configuration/cache/config-redis.md) 預設快取和頁面快取。

## 伺服器設定

本節簡要討論我們建議您為運行應用程式的伺服器考慮的設定。 其中一些設定與應用程式沒有直接關聯；這些僅作為建議提供。

### 日誌旋轉

UNIX `logrotate` 實用程式使您能夠管理生成大量日誌檔案的系統。 它允許自動輪替、壓縮、刪除和郵寄日誌檔案。 每個日誌檔案可以每天、每週、每月或當日誌檔案超過指定大小時進行處理。

有關詳細資訊，請參閱以下內容之一：

* [操作方式：帶十個示例的終極日誌旋轉命令教程](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [堆棧交換](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 手冊頁](https://linuxconfig.org/logrotate-8-manual-page)

### 設定Iptables規則以使各種服務能夠通信

無論您有一台或多台伺服器，都必須開啟防火牆中的埠，以使服務能夠通信。 例如，如果將Solr搜索引擎與Adobe Commerce一起使用，則必須使其能夠與Web伺服器通信。 如果有多個Web節點，則必須使它們能夠相互通信。

更多資訊：

* 烏班圖： [Ubuntu文檔頁](https://help.ubuntu.com/community/IptablesHowTo)。
* CentOS: [CentOS如何操作](https://wiki.centos.org/HowTos/Network/IPTables)。

### 安全增強型Linux(SELinux)規則

我們沒有建議您是否使用SELinux;但是，如果確實使用它，則必須配置服務以與配置iptables類似地彼此通信。

更多資訊：

* 烏班圖： [德比手冊](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS維基](https://wiki.centos.org/HowTos/SELinux)

### 設定電子郵件伺服器

Adobe Commerce和Magento Open Source需要電子郵件伺服器。 我們不建議使用特定的伺服器，但您可以嘗試以下任一操作：

* CentOS的尾碼([數字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)。 [CentOS文檔](https://www.centos.org))
* 烏班圖的尾碼([數字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)。 [Ubuntu文檔](https://help.ubuntu.com/community/MailServer))

### 優化搜索引擎以增強效能：

自2.4.0起，所有安裝都需要Elasticsearch或OpenSearch。

* [安裝和配置搜索引擎](../../configuration/search/overview-search.md)

### 設定消息隊列

自2.3.0版以來，Adobe Commerce和Magento Open Source包括消息隊列功能。 在早期版本中，它只適用於Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 僅Adobe Commerce設定

只有使用Adobe Commerce，您才能配置以下內容：

* [拆分用於簽出、訂單管理和其他資料庫表的資料庫](../../configuration/storage/multi-master.md)
