---
title: PHP設定
description: 按照以下步驟安裝所需的PHP擴展，並配置Adobe Commerce和Magento Open Source的內部安裝所需的PHP設定。
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# PHP設定

本主題討論如何設定所需的PHP選項。

>[!NOTE]
>
>請參閱 [系統要求](../system-requirements.md) 支援的PHP版本。

## 驗證是否已安裝PHP

預設情況下，大多數Linux版本都安裝了PHP。 本主題假定您已經安裝了PHP。 要驗證PHP是否已安裝，請在命令行中鍵入：

```bash
php -v
```

如果安裝了PHP，則會顯示類似於以下消息：

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce和2.4Magento Open Source相容7.3菲律賓比索，但我們與7.4菲律賓比索test，並建議使用。

如果未安裝PHP或需要版本升級，請按照特定Linux版本的說明安裝它。
在CentOS上， [可能需要其他步驟](https://wiki.centos.org/HowTos/php7)。

## 驗證已安裝的擴展

Adobe Commerce和Magento Open Source需要安裝一組擴展。

{{$include /help/_includes/templated/php-extensions.md}}

要驗證已安裝的擴展：

1. 列出已安裝的模組。

   ```bash
   php -m
   ```

1. 驗證是否安裝了所有必需的擴展。
1. 使用用於安裝PHP的相同工作流添加任何缺少的模組。 例如，如果 `yum` 要安裝PHP，可以添加PHP 7.4模組，具體包括：

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## 檢查PHP設定

>[!WARNING]
>
>如果使用PHP 7.4.20，請設定 `pcre.jit=0` 在 `php.ini` 的子菜單。 這可以繞過PHP [漏洞](https://bugs.php.net/bug.php?id=81101) 阻止CSS載入。

- 為PHP設定系統時區；否則，安裝過程中顯示的以下錯誤以及與時間相關的操作（如cron）可能無法正常運行：

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 設定PHP記憶體限制。

   我們的詳細建議包括：

   - 編譯代碼或部署靜態資產， `1G`
   - 調試， `2G`
   - 測試， `~3-4G`

- 增加PHP的值 `realpath_cache_size` 和 `realpath_cache_ttl` 到建議的設定：

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   這些設定允許PHP進程快取檔案路徑，而不是每次載入頁面時查找它們。 請參閱 [效能調整](https://www.php.net/manual/en/ini.core.php) 的子菜單。

- 啟用 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)Adobe Commerce和2.1號Magento Open Source及更高版本所需。

   建議您啟用 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) 出於業績原因。 OPcache在許多PHP分發中啟用。

   Adobe Commerce和Magento Open Source2.1及更高版本使用PHP代碼注釋生成代碼。

>[!NOTE]
>
>為避免在安裝和升級過程中出現問題，強烈建議您對PHP命令行配置和PHP Web伺服器插件配置應用相同的PHP設定。 有關詳細資訊，請參閱下一節。

## 查找PHP配置檔案

本節討論如何找到更新所需設定所需的配置檔案。

### 查找 `php.ini` 配置檔案

要查找Web伺服器配置，請運行 [`phpinfo.php` 檔案](optional-software.md#create-phpinfophp) 在網頁瀏覽器上查找 `Loaded Configuration File` 如下：

![PHP資訊頁](../../assets/installation/config_phpini-webserver.png)

要查找PHP命令行配置，請輸入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果你只有一個 `php.ini` 檔案，在該檔案中進行更改。 如果你有兩個 `php.ini` 檔案，在 *全部* 的子菜單。 如果無法執行此操作，可能會導致無法預料的效能。

### 查找OPcache配置設定

PHP OPcache設定通常位於 `php.ini` 或 `opcache.ini`。 位置可能取決於您的作業系統和PHP版本。 OPcache配置檔案可能具有 `opcache` 部分或設定 `opcache.enable`。

使用以下准則查找它：

- Apache Web伺服器：

   對於具有Apache的Ubuntu,OPcache設定通常位於 `php.ini` 的子菜單。

   對於具有Apache或nginx的CentOS,OPcache設定通常位於 `/etc/php.d/opcache.ini`

   否則，請使用以下命令查找它：

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- nginx Web伺服器，帶PHP-FPM: `/etc/php/7.2/fpm/php.ini`

如果你有多個 `opcache.ini`，修改所有它們。

## 如何設定PHP選項

要設定PHP選項：

1. 開啟 `php.ini` 的子菜單。
1. 在可用的 [時區設定](https://www.php.net/manual/en/timezones.php)
1. 找到以下設定，並取消注釋（如有必要）:

   ```conf
   date.timezone =
   ```

1. 添加您在步驟2中找到的時區設定。

1. 更改 `memory_limit` 到本節開頭建議的值之一。

   比如說，

   ```conf
   memory_limit=2G
   ```

1. 添加或更新 `realpath_cache` 配置以匹配以下值：

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. 保存更改並退出文本編輯器。

1. 開啟另一個 `php.ini` （如果它們不同），並在其中做出相同的更改。

## 設定OPcache選項

設定 `opcache.ini` 選項：

1. 在文本編輯器中開啟OPcache配置檔案：

   - `opcache.ini` (CentOS)
   - `php.ini` （烏班圖）
   - `/etc/php/7.2/fpm/php.ini` (nginx Web伺服器（CentOS或Ubuntu）)

1. 定位 `opcache.save_comments` 必要時取消評論。
1. 確保其值設定為 `1`。
1. 保存更改並退出文本編輯器。
1. 重新啟動Web伺服器：

   - 阿帕奇、烏班圖： `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu和CentOS: `service nginx restart`

## 故障排除

有關PHP問題的故障排除幫助，請參閱以下Adobe Commerce支援文章：

- [在瀏覽器中訪問Adobe Commerce時PHP版本錯誤或404錯誤](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP設定錯誤](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [未正確安裝PHP mcrypt擴展](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本就緒性檢查問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [常見PHP致命錯誤及解決方案](https://support.magento.com/hc/en-us/articles/360030568432)
