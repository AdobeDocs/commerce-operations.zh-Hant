---
title: 使用Apache設定多個網站
description: 請依照本教學課程，使用Apache設定多個網站。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# 使用Apache設定多個網站

我們假設：

如有必要，請複製現有 `index.php` 網站或商店檢視的登入點指令碼，並新增至它：

- 您使用的是開發機器（筆記型電腦、虛擬機等）

   在托管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的托管提供者。

   在雲端基礎架構上設定Adobe Commerce時需要執行其他工作。 完成本主題中討論的任務後，請參閱 [設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎架構商務指南_.

- 每個網站使用一個虛擬主機；虛擬主機配置檔案為 `/etc/httpd/httpd.conf`

   不同作業系統上的不同版本的Apache會以不同的方式設定虛擬主機。 請參閱 [Apache檔案](https://httpd.apache.org/docs/2.4/vhosts) 或網路管理員。

- Commerce軟體安裝在 `/var/www/html/magento2`
- 您有兩個網站，但預設值除外：

   - `french.mysite.mg` 使用網站代碼 `french` 儲存檢視程式碼 `fr`
   - `german.mysite.mg` 使用網站代碼 `german` 儲存檢視程式碼 `de`

## 使用Apache設定多個網站的藍圖

設定多個儲存區包含下列工作：

1. [設定網站、商店和商店檢視](ms-admin.md) 中。
1. 建立 [Apache虛擬主機](#step-2-create-apache-virtual-hosts) 每個商務網站。

## 步驟1:在管理員中建立網站、儲存和儲存檢視

請參閱 [在管理員中設定多個網站、商店和儲存檢視](ms-admin.md).

## 步驟2:建立Apache虛擬主機

本節探討如何為 `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 使用Apache伺服器變數 `SetEnvIf` 在虛擬主機中。

如需 `SetEnvIf`，請參閱：

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**建立Apache虛擬主機的方式**:

1. 身為使用者 `root` 權限，在文本編輯器中開啟虛擬主機配置檔案。

   例如，開啟 `/etc/httpd/conf/httpd.conf`

1. 找出區段，開頭為 `<VirtualHost *:80>`.
1. 在任何現有虛擬主機之後建立下列虛擬主機：

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. 將變更儲存至 `httpd.conf` 並退出文字編輯器。
1. 重新啟動Apache:

   - CentOS: `service httpd restart`
   - 烏本圖： `service apache2 restart`

## 驗證您的網站

除非您已為商店的URL設定DNS，否則您必須新增靜態路由至您 `hosts` 檔案：

1. 找到您的作業系統 `hosts` 檔案。
1. 以下格式添加靜態路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 在瀏覽器中前往下列其中一個URL:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在托管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的托管提供者。
>- 在雲端基礎架構上設定Adobe Commerce需要執行其他工作；請參閱 [設定多個雲端網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎架構商務指南_.


### 疑難排解

- 如果您的法文和德文網站傳回404s，但管理員載入，請確定您已完成 [步驟6:將存放區代碼新增至基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都傳回404，請確定您重新啟動了Web伺服器。
- 如果管理員無法正常運作，請確定您已正確設定虛擬主機。
