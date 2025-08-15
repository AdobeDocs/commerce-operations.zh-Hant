---
title: 使用Apache設定多個網站
description: 按照本教學課程中的說明使用Apache設定多個網站。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# 使用Apache設定多個網站

我們假設：

如有必要，請複製網站或商店檢視的現有`index.php`進入點指令碼，並新增下列內容：

- 您正在使用開發機器（筆記型電腦、虛擬機器器等）

  在託管環境中部署多個網站可能需要執行其他工作；請洽詢您的託管提供者，以取得詳細資訊。

  在雲端基礎結構上設定Adobe Commerce需要其他工作。 完成本主題中討論的工作後，請參閱[雲端基礎結構上的Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hant)中的&#x200B;_設定多個網站或商店_。

- 您對每個網站使用一個虛擬主機；虛擬主機設定檔為`/etc/httpd/httpd.conf`

  不同作業系統上的不同Apache版本會以不同方式設定虛擬主機。 如果您不確定如何設定虛擬主機，請參閱[Apache檔案](https://httpd.apache.org/docs/2.4/vhosts)或網路管理員。

- 已在`/var/www/html/magento2`中安裝Commerce軟體
- 您有預設以外的兩個網站：

   - 網站代碼為`french.mysite.mg`且商店檢視代碼為`french`的`fr`
   - 網站代碼為`german.mysite.mg`且商店檢視代碼為`german`的`de`

## 使用Apache設定多個網站的藍圖

設定多個存放區包含下列工作：

1. [在Admin中設定網站、商店和商店檢視](ms-admin.md)。
1. 為每個Commerce網站建立一個[Apache虛擬主機](#step-2-create-apache-virtual-hosts)。

## 步驟1：在「管理員」中建立網站、商店和商店檢視

請參閱[在Admin](ms-admin.md)中設定多個網站、商店和商店檢視。

## 步驟2：建立Apache虛擬主機

本節討論如何在虛擬主機中使用Apache伺服器變數`MAGE_RUN_TYPE`設定`MAGE_RUN_CODE`和`SetEnvIf`的值。

如需`SetEnvIf`的詳細資訊，請參閱：

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**若要建立Apache虛擬主機**：

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟虛擬主機設定檔。

   例如，開啟`/etc/httpd/conf/httpd.conf`

1. 找到以`<VirtualHost *:80>`開頭的區段。
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

1. 將變更儲存至`httpd.conf`並結束文字編輯器。
1. 重新啟動Apache：

   - CentOS： `service httpd restart`
   - Ubuntu： `service apache2 restart`

## 驗證您的網站

除非您已為存放區的URL設定DNS，否則您必須在`hosts`檔案中新增靜態路由至主機：

1. 找到您的作業系統`hosts`檔案。
1. 以格式新增靜態路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 前往瀏覽器中的下列URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在託管環境中部署多個網站可能需要執行其他工作；請洽詢您的託管提供者，以取得詳細資訊。
>- 在雲端基礎結構上設定Adobe Commerce需要其他工作；請參閱[雲端基礎結構上的Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hant)中的&#x200B;_設定多個雲端網站或商店_。

### 疑難排解

- 如果您的法文和德文網站傳回404s，但您的管理員載入，請確定您已完成[步驟6：將商店程式碼新增至基底URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url)。
- 如果所有URL都傳回404s，請確定您已重新啟動網頁伺服器。
- 如果管理員無法正常運作，請確定您正確設定虛擬主機。
