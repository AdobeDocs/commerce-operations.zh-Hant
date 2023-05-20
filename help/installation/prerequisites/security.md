---
title: 本地安裝安全性
description: 瞭解如何改進Adobe Commerce或Magento Open Source內部安裝的安全狀態。
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 本地安裝安全性

[安全增強型Linux(SELinux)](https://selinuxproject.org/page/Main_Page) 使CentOS和Ubuntu管理員能夠更好地控制其伺服器的訪問。 如果使用SELinux *和* Apache必須啟動到另一台主機的連接，您必須運行本節中討論的命令。

>[!NOTE]
>
>Adobe對使用SELinux沒有建議；如果需要，可以將其用於增強的安全性。 如果使用SELinux，則必須正確配置它，否則Adobe Commerce和Magento Open Source可以不可預知地運行。 如果選擇使用SELinux，請咨詢資源，如 [CentOS維基](https://wiki.centos.org/HowTos/SELinux) 設定規則以啟用通信。

## 使用Apache安裝的建議

如果選擇啟用SELinux，則運行安裝程式時可能遇到問題，除非更改 *安全上下文* 的下一頁：

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

以上命令僅適用於Apache Web伺服器。 由於配置和安全要求的多樣性，我們不能保證這些命令在所有情況下都能正常工作。 有關詳細資訊，請參閱：

* [手冊頁](https://linux.die.net/man/8/httpd_selinux)
* [伺服器實驗室](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 啟用伺服器間通信

如果Apache和資料庫伺服器位於同一主機上，則如果計畫使用使用整合的 `curl` (例如 Paypal和USPS)。
要啟用Apache啟動到啟用了SELinux的另一台主機的連接，請執行以下操作：

1. 要確定是否啟用了SELinux，請使用以下命令：

   ```bash
   getenforce
   ```

   `Enforcing` 顯示以確認SELinux正在運行。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * 烏班圖： `setsebool -P apache2_can_network_connect=1`

## 開啟防火牆中的埠

根據您的安全要求，您可能會發現有必要在防火牆中開啟埠80和其他埠。 由於網路安全的敏感性，Adobe強烈建議您在繼續操作之前先與IT部門協商。 以下是一些建議的參考：

* 烏班圖： [Ubuntu文檔頁](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS如何操作](https://wiki.centos.org/HowTos/Network/IPTables)。
