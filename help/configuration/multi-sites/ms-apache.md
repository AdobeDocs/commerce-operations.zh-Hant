---
title: 使用Apache設定多個網站
description: 按照本教程，使用Apache設定多個網站。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# 使用Apache設定多個網站

我們假設：

如有必要，請複製現有 `index.php` 網站或 [商店視圖](https://glossary.magento.com/store-view) 並添加以下內容：

- 您正在使用開發機器（筆記型電腦、虛擬機等）

   在托管環境中部署多個網站可能需要執行其他任務；有關詳細資訊，請與托管提供商聯繫。

   在雲基礎架構上設定Adobe Commerce需要其他任務。 完成本主題中討論的任務後，請參見 [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 的 _Commerce Cloud指南_。

- 每個網站使用一個虛擬主機；虛擬主機配置檔案為 `/etc/httpd/httpd.conf`

   不同作業系統上不同版本的Apache設定虛擬主機的方式不同。 咨詢 [Apache文檔](https://httpd.apache.org/docs/2.4/vhosts) 或網路管理員。

- Commerce軟體安裝在 `/var/www/html/magento2`
- 您有兩個非預設網站：

   - `french.mysite.mg` 使用網站代碼 `french` 和儲存視圖代碼 `fr`
   - `german.mysite.mg` 使用網站代碼 `german` 和儲存視圖代碼 `de`

## 使用Apache設定多個網站的路線圖

設定多個儲存由以下任務組成：

1. [設定網站、商店和商店視圖](ms-admin.md) 的子菜單。
1. 建立一個 [Apache虛擬主機](#step-2-create-apache-virtual-hosts) 按商務網站。

## 步驟1:在管理員中建立網站、商店和商店視圖

請參閱 [在管理員中設定多個網站、商店和商店視圖](ms-admin.md)。

## 步驟2:建立Apache虛擬主機

本節討論如何設定 `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 使用Apache伺服器變數 `SetEnvIf` 在虛擬主機中。

有關 `SetEnvIf`，請參閱：

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**建立Apache虛擬主機**:

1. 作為用戶 `root` 權限，在文本編輯器中開啟虛擬主機配置檔案。

   例如，開啟 `/etc/httpd/conf/httpd.conf`

1. 找到節的開頭 `<VirtualHost *:80>`。
1. 在任何現有虛擬主機後建立以下虛擬主機：

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

1. 將更改保存到 `httpd.conf` 並退出文本編輯器。
1. 重新啟動Apache:

   - CentOS: `service httpd restart`
   - 烏班圖： `service apache2 restart`

## 驗證您的站點

除非您為商店的URL設定了DNS，否則必須向您的商店中的主機添加靜態路由 `hosts` 檔案：

1. 找到您的作業系統 `hosts` 的子菜單。
1. 以下格式添加靜態路由：

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. 在瀏覽器中轉到以下URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在托管環境中部署多個網站可能需要執行其他任務；有關詳細資訊，請與托管提供商聯繫。
>- 在雲基礎架構上設定Adobe Commerce需要執行其他任務；見 [設定多個雲網站或儲存](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 的 _Commerce Cloud指南_。


### 故障排除

- 如果您的法語和德語站點返回404s，但您的管理員載入，請確保您已完成 [步驟6:將儲存代碼添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url)。
- 如果所有URL都返回404s，請確保重新啟動了Web伺服器。
- 如果管理員無法正常工作，請確保正確設定虛擬主機。
