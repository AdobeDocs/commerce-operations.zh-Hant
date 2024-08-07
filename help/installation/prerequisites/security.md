---
title: 內部部署安裝安全性
description: 瞭解改善Adobe Commerce內部部署安裝之安全性狀態的方法。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 內部部署安裝安全性

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page)讓CentOS和Ubuntu管理員能夠更深入控制其伺服器。 如果您使用SELinux *和* Apache必須起始與另一台主機的連線，您必須執行本節中討論的命令。

>[!NOTE]
>
>Adobe對使用SELinux沒有任何建議；您可以視需要將其用於增強安全性。 如果您使用SELinux，則必須正確設定，否則Adobe Commerce會無法預期地運作。 如果您選擇使用SELinux，請洽詢[CentOS wiki](https://wiki.centos.org/HowTos/SELinux)之類的資源，以設定規則來啟用通訊。

## 有關使用Apache安裝的建議

如果您選擇啟用SELinux，除非您變更某些目錄的&#x200B;*安全性內容*，否則執行安裝程式時可能會發生問題，如下所示：

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

上述命令僅適用於Apache Web Server。 由於各種設定和安全要求，我們並不保證這些命令在任何情況下都有效。 如需詳細資訊，請參閱：

* [線上手冊](https://linux.die.net/man/8/httpd_selinux)
* [伺服器實驗室](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 啟用伺服器間通訊

如果Apache和資料庫伺服器位於相同主機上，如果您打算使用使用`curl`的整合(例如 Paypal和USPS)。
若要讓Apache在啟用SELinux的情況下起始與其他主機的連線：

1. 若要判斷是否已啟用SELinux，請使用下列指令：

   ```bash
   getenforce
   ```

   顯示`Enforcing`以確認SELinux正在執行。

   * CentOS： `setsebool -P httpd_can_network_connect=1`
   * Ubuntu： `setsebool -P apache2_can_network_connect=1`

## 在防火牆中開啟連線埠

根據您的安全性需求，您可能會發現有必要開啟防火牆中的連線埠80和其他連線埠。 由於網路安全的敏感性質，Adobe強烈建議您先洽詢IT部門，再繼續進行。 以下是一些建議的參考資料：

* Ubuntu： [Ubuntu檔案頁面](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS： [CentOS操作說明](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。
