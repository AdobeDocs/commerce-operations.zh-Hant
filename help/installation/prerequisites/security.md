---
title: 本地安裝安全
description: 了解如何改善Adobe Commerce的安全態勢，或Magento Open Source內部部署。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# 本地安裝安全

[安全增強Linux(SELinux)](https://selinuxproject.org/page/Main_Page) 使CentOS和Ubuntu管理員能夠更好地控制其伺服器的訪問。 如果您使用SELinux *和* Apache必須啟動到另一台主機的連接，您必須運行本節中討論的命令。

>[!NOTE]
>
>Adobe不建議使用SELinux;如有需要，您可將其用於增強安全性。 如果您使用SELinux，則必須正確配置，否則Adobe Commerce和Magento Open Source可能無法預測地運作。 如果您選擇使用SELinux，請查詢資源，例如 [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux) 設定規則以啟用通訊。

## 使用Apache進行安裝的建議

如果選擇啟用SELinux，則運行安裝程式時可能遇到問題，除非您更改 *安全上下文* 按如下所示：

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

前面的命令只能與Apache Web伺服器一起使用。 由於配置和安全要求多種多樣，我們不能保證這些命令在所有情況下都能正常工作。 如需詳細資訊，請參閱：

* [手冊頁](https://linux.die.net/man/8/httpd_selinux)
* [伺服器實驗室](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 啟用伺服器間通信

如果Apache和資料庫伺服器位於同一台主機上，如果您打算使用使用的整合，請使用下列命令 `curl` (例如 Paypal和USPS)。
要啟用Apache以啟用SELinux啟動到另一台主機的連接，請執行以下操作：

1. 要確定是否啟用SELinux，請使用以下命令：

   ```bash
   getenforce
   ```

   `Enforcing` 顯示以確認SELinux正在執行。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * 烏本圖： `setsebool -P apache2_can_network_connect=1`

## 在防火牆中開啟埠

根據您的安全要求，您可能會發現需要在防火牆中開啟埠80和其他埠。 由於網路安全性的敏感性，Adobe強烈建議您在繼續操作前先與IT部門協商。 以下是一些建議的參考：

* 烏本圖： [Ubuntu檔案頁面](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS作法](https://wiki.centos.org/HowTos/Network/IPTables).
