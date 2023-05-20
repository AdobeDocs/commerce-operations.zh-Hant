---
title: 使用Nginx設定多個網站
description: 按照本教程設定使用Nginx的多個網站。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# 使用Nginx設定多個網站

我們假設：

- 您正在使用開發機器（筆記型電腦、虛擬機或類似設備）。

   在托管環境中部署多個網站可能需要執行其他任務；有關詳細資訊，請與托管提供商聯繫。

   在雲基礎架構上設定Adobe Commerce需要其他任務。 完成本主題中討論的任務後，請參見 [設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 的 _雲基礎架構上的商務指南_。

- 您在一個虛擬主機檔案中接受多個域，或者每個網站使用一個虛擬主機；虛擬主機配置檔案位於 `/etc/nginx/sites-available`。
- 使用 `nginx.conf.sample` 僅提供本教程中討論的修改。
- Commerce軟體安裝在 `/var/www/html/magento2`。
- 您有兩個非預設網站：

   - `french.mysite.mg` 使用網站代碼 `french` 和儲存視圖代碼 `fr`
   - `german.mysite.mg` 使用網站代碼 `german` 和儲存視圖代碼 `de`
   - `mysite.mg` 是預設網站和預設商店視圖

>[!TIP]
>
>請參閱 [建立網站](ms-admin.md#step-2-create-websites) 和 [建立儲存視圖](ms-admin.md#step-4-create-store-views) 來查找這些值。

下面是用nginx設定多個網站的路線圖：

1. [設定網站、商店和商店視圖](ms-admin.md) 的子菜單。
1. 建立 [Nginx虛擬主機](#step-2-create-nginx-virtual-hosts))以映射多個網站或每個Commerce網站的一個Nginx虛擬主機（下面的詳細步驟）。
1. 傳遞 [MAGE變數](ms-overview.md) `$MAGE_RUN_TYPE` 和 `$MAGE_RUN_CODE` 使用提供的Magento `nginx.conf.sample` （下面詳細步驟）。

   - `$MAGE_RUN_TYPE` 可以 `store` 或 `website`:

      - 使用 `website` 把你的網站裝進你的店面。
      - 使用 `store` 將任何商店視圖載入到店面。
   - `$MAGE_RUN_CODE` 是與 `$MAGE_RUN_TYPE`。


1. 在Commerce管理員上更新基本URL配置。

## 步驟1:在管理員中建立網站、商店和商店視圖

請參閱 [在管理員中設定多個網站、商店和商店視圖](ms-admin.md)。

## 步驟2:建立nginx虛擬主機

此步驟討論如何在店面上載入網站。 您可以使用網站或商店視圖；如果使用儲存視圖，則必須相應調整參數值。 您必須以用戶身份完成本節中的任務 `sudo` 權限。

只使用一個 [nginx虛擬主機檔案](#step-2-create-nginx-virtual-hosts)，您可以保持nginx配置簡單且乾淨。 通過使用多個虛擬主機檔案，您可以自定義每個儲存(以使用 `french.mysite.mg` 例如)。

**建立一個虛擬主機** （簡化）:

此配置在 [nginx配置](../../installation/prerequisites/web-server/nginx.md)。

1. 開啟文本編輯器，並將下列內容添加到名為 `/etc/nginx/sites-available/magento`:

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

1. 保存對檔案的更改並退出文本編輯器。
1. 驗證伺服器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，將顯示以下消息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機配置檔案的語法。

1. 在 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

有關map指令的詳細資訊，請參見 [map指令上的nginx文檔](http://nginx.org/en/docs/http/ngx_http_map_module.html#map)。


**建立多個虛擬主機**:

1. 開啟文本編輯器，並將下列內容添加到名為 `/etc/nginx/sites-available/french.mysite.mg`:

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

1. 建立另一個名為 `german.mysite.mg` 位於同一目錄中，並包含以下內容：

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

1. 保存對檔案的更改並退出文本編輯器。
1. 驗證伺服器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，將顯示以下消息：

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

## 第3步：修改nginx.conf.sample

>[!TIP]
>
>不編輯 `nginx.conf.sample` 檔案；它是一個核心Commerce檔案，可以隨每個新版本一起更新。 而是複製 `nginx.conf.sample` 檔案，更名它，然後編輯複製的檔案。

**編輯主應用程式的PHP入口點**:

修改 `nginx.conf.sample` 檔案**:

1. 開啟文本編輯器並查看 `nginx.conf.sample` 檔案`<magento2_installation_directory>/nginx.conf.sample`。 查找以下部分：

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

1. 更新 `nginx.conf.sample` 在include語句前具有以下兩行的檔案：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

主應用程式的更新PHP入口點示例如下：

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

## 第4步：更新基本URL配置

您必須更新的 `french` 和 `german` Commerce admin中的網站。

### 更新法文網站基URL

1. 登錄到Commerce管理員並導航到 **商店** > **設定** > **配置** > **常規** > **Web**。
1. 更改 _配置範圍_ 到 `french` 的子菜單。
1. 展開 **基本URL** 部分並更新 **基本URL** 和 **基本連結URL** 值 `http://french.magento24.com/`。
1. 展開 **基本URL（安全）** 部分並更新 **安全基URL** 和 **安全基本連結URL** 值 `https://french.magento24.com/`。
1. 按一下 **保存配置** 並保存配置更改。

### 更新德語網站基URL

1. 登錄到Commerce管理員並導航到 **商店** > **設定** > **配置** > **常規** > **Web**。
1. 更改 _配置範圍_ 到 `german` 的子菜單。
1. 展開 **基本URL** 部分並更新 **基本URL** 和 **基本連結URL** 值 `http://german.magento24.com/`。
1. 展開 **基本URL（安全）** 部分並更新 **安全基URL** 和 **安全基本連結URL** 值 `https://german.magento24.com/`。
1. 按一下 **保存配置** 並保存配置更改。

### 清除快取

運行以下命令清除 `config` 和 `full_page` 快取。

```bash
bin/magento cache:clean config full_page
```

## 驗證您的站點

除非您為商店的URL設定了DNS，否則必須向您的商店中的主機添加靜態路由 `hosts` 檔案：

1. 找到您的作業系統 `hosts` 的子菜單。
1. 以下格式添加靜態路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
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
>- 在雲基礎架構上設定Adobe Commerce需要執行其他任務；見 [設定多個雲網站或儲存](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 的 _雲基礎架構上的商務指南_。


### 故障排除

- 如果您的法語和德語站點返回404s，但您的管理員載入，請確保您已完成 [步驟6:將儲存代碼添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url)。
- 如果所有URL都返回404s，請確保重新啟動了Web伺服器。
- 如果管理員無法正常工作，請確保正確設定虛擬主機。
