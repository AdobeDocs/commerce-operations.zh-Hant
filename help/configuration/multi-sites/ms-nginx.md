---
title: 使用Nginx設定多個網站
description: 按照本教學課程中的說明使用Nginx設定多個網站。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# 使用Nginx設定多個網站

我們假設：

- 您使用開發機器（筆記型電腦、虛擬機器器或類似裝置）。

  在託管環境中部署多個網站可能需要執行其他工作；請洽詢您的託管提供者，以取得詳細資訊。

  在雲端基礎結構上設定Adobe Commerce需要其他工作。 完成本主題中討論的工作後，請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html)。

- 您在一個虛擬主機檔案中接受多個網域，或每個網站使用一個虛擬主機；虛擬主機組態檔位於`/etc/nginx/sites-available`。
- 您僅使用本教學課程中討論的修改內容，再使用Commerce提供的`nginx.conf.sample`。
- 已在`/var/www/html/magento2`中安裝Commerce軟體。
- 您有預設以外的兩個網站：

   - 網站代碼為`french`且商店檢視代碼為`fr`的`french.mysite.mg`
   - 網站代碼為`german`且商店檢視代碼為`de`的`german.mysite.mg`
   - `mysite.mg`是預設網站和預設商店檢視

>[!TIP]
>
>如需尋找這些值的說明，請參閱[建立網站](ms-admin.md#step-2-create-websites)和[建立商店檢視](ms-admin.md#step-4-create-store-views)。

以下是使用nginx設定多個網站的藍圖：

1. [在Admin中設定網站、商店和商店檢視](ms-admin.md)。
1. 建立[Nginx虛擬主機](#step-2-create-nginx-virtual-hosts))，以對應多個網站或每個Commerce網站一個Nginx虛擬主機（詳細步驟如下）。
1. 使用Magento提供的`nginx.conf.sample`將[MAGE變數](ms-overview.md) `$MAGE_RUN_TYPE`和`$MAGE_RUN_CODE`的值傳遞給nginx （詳細步驟如下）。

   - `$MAGE_RUN_TYPE`可以是`store`或`website`：

      - 使用`website`在您的店面中載入您的網站。
      - 使用`store`載入您店面中的任何商店檢視。

   - `$MAGE_RUN_CODE`是與`$MAGE_RUN_TYPE`對應的唯一網站或商店檢視代碼。

1. 更新Commerce管理員的基本URL設定。

## 步驟1：在「管理員」中建立網站、商店和商店檢視

請參閱[在Admin](ms-admin.md)中設定多個網站、商店和商店檢視。

## 步驟2：建立nginx虛擬主機

此步驟會討論如何在店面載入網站。 您可以使用網站或商店檢視；如果您使用商店檢視，則必須適當地調整引數值。 您必須以具有`sudo`許可權的使用者身分完成此段落中的工作。

只要使用一個[nginx虛擬主機檔案](#step-2-create-nginx-virtual-hosts)，您就可以讓nginx組態簡單整潔。 使用數個虛擬主機檔案，您就可以自訂每個存放區（以使用自訂位置執行`french.mysite.mg`）。

**若要建立一個虛擬主機** （簡化）：

此組態會展開至[nginx組態](../../installation/prerequisites/web-server/nginx.md)。

1. 開啟文字編輯器，並將下列內容新增至名為`/etc/nginx/sites-available/magento`的新檔案：

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 將變更儲存至檔案並退出文字編輯器。
1. 驗證伺服器組態：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機組態檔的語法。

1. 在`/etc/nginx/sites-enabled`目錄中建立符號連結：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

如需有關對應指示詞的詳細資訊，請參閱對應指示詞[&#128279;](http://nginx.org/en/docs/http/ngx_http_map_module.html#map)上的nginx檔案。


**若要建立多個虛擬主機**：

1. 開啟文字編輯器，並將下列內容新增至名為`/etc/nginx/sites-available/french.mysite.mg`的新檔案：

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 在相同目錄中建立另一個名為`german.mysite.mg`的檔案，其內容如下：

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 將變更儲存至檔案並退出文字編輯器。
1. 驗證伺服器組態：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機組態檔的語法。

1. 在`/etc/nginx/sites-enabled`目錄中建立符號連結：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 步驟3：修改nginx.conf.sample

>[!TIP]
>
>請勿編輯`nginx.conf.sample`檔案；它是核心Commerce檔案，可能會隨著每個新發行版本而更新。 請改為複製`nginx.conf.sample`檔案、重新命名，然後編輯複製的檔案。

**若要編輯主要應用程式的PHP進入點**：

若要修改`nginx.conf.sample`檔案**：

1. 開啟文字編輯器並檢閱`nginx.conf.sample`檔案，`<magento2_installation_directory>/nginx.conf.sample`。 尋找下列章節：

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. 在include陳述式前使用以下兩行更新`nginx.conf.sample`檔案：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

更新主要應用程式的PHP進入點的範例如下所示：

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## 步驟4：更新基底URL設定

您必須在Commerce管理員中更新`french`和`german`網站的基底URL。

### 更新法文網站基底URL

1. 登入Commerce管理員並瀏覽至&#x200B;**商店** > **設定** > **設定** > **一般** > **網頁**。
1. 將&#x200B;_設定範圍_&#x200B;變更為`french`網站。
1. 展開&#x200B;**基底URL**&#x200B;區段，並將&#x200B;**基底URL**&#x200B;和&#x200B;**基底連結URL**&#x200B;值更新為`http://french.magento24.com/`。
1. 展開&#x200B;**基礎URL （安全）**&#x200B;區段，並將&#x200B;**安全基礎URL**&#x200B;和&#x200B;**安全基礎連結URL**&#x200B;值更新為`https://french.magento24.com/`。
1. 按一下&#x200B;**儲存組態**&#x200B;並儲存組態變更。

### 更新德文網站基底URL

1. 登入Commerce管理員並瀏覽至&#x200B;**商店** > **設定** > **設定** > **一般** > **網頁**。
1. 將&#x200B;_設定範圍_&#x200B;變更為`german`網站。
1. 展開&#x200B;**基底URL**&#x200B;區段，並將&#x200B;**基底URL**&#x200B;和&#x200B;**基底連結URL**&#x200B;值更新為`http://german.magento24.com/`。
1. 展開&#x200B;**基礎URL （安全）**&#x200B;區段，並將&#x200B;**安全基礎URL**&#x200B;和&#x200B;**安全基礎連結URL**&#x200B;值更新為`https://german.magento24.com/`。
1. 按一下&#x200B;**儲存組態**&#x200B;並儲存組態變更。

### 清除快取

執行以下命令以清除`config`和`full_page`快取。

```bash
bin/magento cache:clean config full_page
```

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
>- 在雲端基礎結構上設定Adobe Commerce需要其他工作；請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[設定多個雲端網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html)。

### 疑難排解

- 如果您的法文和德文網站傳回404s，但您的管理員載入，請確定您已完成[步驟6：將商店程式碼新增至基底URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url)。
- 如果所有URL都傳回404s，請確定您已重新啟動網頁伺服器。
- 如果管理員無法正常運作，請確定您正確設定虛擬主機。
