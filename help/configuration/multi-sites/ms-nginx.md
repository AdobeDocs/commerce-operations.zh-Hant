---
title: 使用Nginx設定多個網站
description: 請依照本教學課程，使用Nginx設定多個網站。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 0%

---


# 使用Nginx設定多個網站

我們假設：

- 您使用的是開發機器（筆記型電腦、虛擬機或類似機器）。

   在托管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的托管提供者。

   在雲端基礎架構上設定Adobe Commerce時需要執行其他工作。 完成本主題中討論的任務後，請參閱 [設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎架構商務指南_.

- 您在一個虛擬主機檔案中接受多個域，或為每個網站使用一個虛擬主機；虛擬主機配置檔案位於 `/etc/nginx/sites-available`.
- 您使用 `nginx.conf.sample` 由Commerce提供，且僅包含本教學課程中討論的修改。
- Commerce軟體安裝在 `/var/www/html/magento2`.
- 您有兩個網站，但預設值除外：

   - `french.mysite.mg` 使用網站代碼 `french` 儲存檢視程式碼 `fr`
   - `german.mysite.mg` 使用網站代碼 `german` 儲存檢視程式碼 `de`
   - `mysite.mg` 是預設網站和預設商店檢視

>[!TIP]
>
>請參閱 [建立網站](ms-admin.md#step-2-create-websites) 和 [建立商店檢視](ms-admin.md#step-4-create-store-views) 以協助您找到這些值。

以下是使用原始碼設定多個網站的藍圖：

1. [設定網站、商店和商店檢視](ms-admin.md) 中。
1. 建立 [Nginx虛擬主機](#step-2-create-nginx-virtual-hosts))，以對應多個網站或每個商務網站一個Nginx虛擬主機（如下所述步驟）。
1. 傳遞 [MAGE變數](ms-overview.md) `$MAGE_RUN_TYPE` 和 `$MAGE_RUN_CODE` 使用提供的Magento `nginx.conf.sample` （詳細步驟如下）。

   - `$MAGE_RUN_TYPE` 可以是 `store` 或 `website`:

      - 使用 `website` 來載入您的店面。
      - 使用 `store` 來載入店面中的任何商店檢視。
   - `$MAGE_RUN_CODE` 是與 `$MAGE_RUN_TYPE`.


1. 在商務管理員上更新基礎URL設定。

## 步驟1:在管理員中建立網站、儲存和儲存檢視

請參閱 [在管理員中設定多個網站、商店和儲存檢視](ms-admin.md).

## 步驟2:建立原始虛擬主機

此步驟探討如何在 [店面](https://glossary.magento.com/storefront). 您可以使用網站或儲存檢視；如果使用商店視圖，則必須相應地調整參數值。 您必須以使用者身分，完成本節中的工作 `sudo` 權限。

只使用一個 [nginx虛擬主機檔案](#step-2-create-nginx-virtual-hosts)，您可以讓nginx設定簡單明瞭。 使用數個虛擬主機檔案，您可以自訂每個存放區(以針對 `french.mysite.mg` 例如)。

**建立一個虛擬主機** （簡化）:

此設定會在 [nginx配置](../../installation/prerequisites/web-server/nginx.md).

1. 開啟文字編輯器，並將下列內容新增至名為的新檔案 `/etc/nginx/sites-available/magento`:

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

1. 將變更儲存至檔案，然後退出文字編輯器。
1. 驗證伺服器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機配置檔案的語法。

1. 在中建立符號連結 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

有關映射指令的詳細資訊，請參見 [映射指令的nginx文檔](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**建立多個虛擬主機**:

1. 開啟文字編輯器，並將下列內容新增至名為的新檔案 `/etc/nginx/sites-available/french.mysite.mg`:

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

1. 建立另一個名為 `german.mysite.mg` 包含下列內容的同一目錄：

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

1. 將變更儲存至檔案，然後退出文字編輯器。
1. 驗證伺服器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機配置檔案的語法。

1. 在 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 步驟3:修改nginx.conf.sample

>[!TIP]
>
>請勿編輯 `nginx.conf.sample` 檔案；這是核心商務檔案，可隨每次新發行更新。 請改為複製 `nginx.conf.sample` 檔案，重新命名，然後編輯複製的檔案。

**編輯主應用程式的PHP入口點**:

若要修改 `nginx.conf.sample` 檔案**:

1. 開啟文字編輯器並檢閱 `nginx.conf.sample` 檔案，`<magento2_installation_directory>/nginx.conf.sample`. 查看下列章節：

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

1. 更新 `nginx.conf.sample` 檔案中，在include陳述式前面加上下列兩行：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

更新主應用程式的PHP入口點的示例如下：

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

## 步驟4:更新基本URL設定

您必須更新 `french` 和 `german` 網站。

### 更新法文網站基礎URL

1. 登入商務管理員並導覽至 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 變更 _配置範圍_ 到 `french` 網站。
1. 展開 **基本URL** 區段和更新 **基本URL** 和 **基本連結URL** 值 `http://french.magento24.com/`.
1. 展開 **基本URL（安全）** 區段和更新 **安全基URL** 和 **安全基礎連結URL** 值 `https://french.magento24.com/`.
1. 按一下 **儲存設定** 並儲存設定變更。

### 更新德文網站基礎URL

1. 登入商務管理員並導覽至 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 變更 _配置範圍_ 到 `german` 網站。
1. 展開 **基本URL** 區段和更新 **基本URL** 和 **基本連結URL** 值 `http://german.magento24.com/`.
1. 展開 **基本URL（安全）** 區段和更新 **安全基URL** 和 **安全基礎連結URL** 值 `https://german.magento24.com/`.
1. 按一下 **儲存設定** 並儲存設定變更。

### 清除快取

執行下列命令以清除 `config` 和 `full_page` 快取。

```bash
bin/magento cache:clean config full_page
```

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
