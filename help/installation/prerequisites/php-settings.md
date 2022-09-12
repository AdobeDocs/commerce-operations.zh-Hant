---
title: PHP設定
description: 請按照以下步驟安裝所需的PHP擴展，並為Adobe Commerce和Magento Open Source的本地安裝配置所需的PHP設定。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# PHP設定

本主題討論如何設定必要項目 [PHP](https://glossary.magento.com/php) 選項。

>[!NOTE]
>
>請參閱 [系統需求](../system-requirements.md) 以了解PHP的支援版本。

## 驗證PHP是否已安裝

預設情況下，大多數類型的Linux都安裝了PHP。 本主題假定您已安裝PHP。 要驗證是否已安裝PHP，請在命令行中鍵入：

```bash
php -v
```

若 [PHP](https://glossary.magento.com/php) 已安裝，則會顯示類似下列的訊息：

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce和Magento Open Source2.4與PHP 7.3相容，但我們使用PHP 7.4進行測試，並建議您使用。

如果未安裝PHP或需要版本升級，請按照特定Linux版本的說明安裝它。
在CentOS上， [可能需要其他步驟](https://wiki.centos.org/HowTos/php7).

## 驗證已安裝的擴充功能

Adobe Commerce和Magento Open Source需要安裝一組擴充功能。

{{$include /help/_includes/php-extensions.md}}

若要驗證已安裝的擴充功能：

1. 列出已安裝的模組。

   ```bash
   php -m
   ```

1. 確認已安裝所有必要的擴充功能。
1. 使用用於安裝PHP的相同工作流添加任何缺少的模組。 例如，若您使用 `yum` 要安裝PHP，可以添加PHP 7.4模組，其中包括：

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## 檢查PHP設定

>[!WARNING]
>
>如果使用PHP 7.4.20，請設定 `pcre.jit=0` 在 `php.ini` 檔案。 這可以繞過PHP [錯誤](https://bugs.php.net/bug.php?id=81101) 來防止CSS載入。

- 為PHP設定系統時區；否則，安裝期間可能無法顯示下列錯誤，以及cron等與時間相關的操作：

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 設定PHP記憶體限制。

   我們的詳細建議包括：

   - 編譯程式碼或部署靜態資產， `1G`
   - 除錯， `2G`
   - 測試， `~3-4G`

- 增加PHP的值 `realpath_cache_size` 和 `realpath_cache_ttl` 至建議的設定：

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   這些設定可讓PHP程式快取檔案的路徑，而非每次頁面載入時查詢路徑。 請參閱 [效能調整](https://www.php.net/manual/en/ini.core.php) 在PHP文檔中。

- 啟用 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)，此為Adobe Commerce和Magento Open Source2.1及更新版本的必要項目。

   建議您啟用 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) 出於表現原因。 在許多PHP分發中啟用了OPcache。

   Adobe Commerce和Magento Open Source2.1及更新版本使用PHP程式碼註解來產生程式碼。

>[!NOTE]
>
>為避免在安裝和升級期間出現問題，我們強烈建議您將相同的PHP設定應用於PHP命令行配置和PHP Web伺服器插件配置。 如需詳細資訊，請參閱下一節。

## 查找PHP配置檔案

本節探討如何找到更新所需設定所需的配置檔案。

### 查找 `php.ini` 組態檔

要查找Web伺服器配置，請運行 [`phpinfo.php` 檔案](optional-software.md#create-phpinfophp) 在網頁瀏覽器上尋找 `Loaded Configuration File` 如下所示：

![PHP資訊頁](../../assets/installation/config_phpini-webserver.png)

要定位PHP命令行配置，請輸入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果你只有一個 `php.ini` 檔案中進行更改。 如果你有兩個 `php.ini` 檔案，請在 *all* 檔案。 若無法這麼做，可能會導致無法預測的效能。

### 查找OPcache配置設定

PHP OPcache設定通常位於 `php.ini` 或 `opcache.ini`. 位置可能取決於您的作業系統和PHP版本。 OPcache配置檔案可能具有 `opcache` 區段或設定，如 `opcache.enable`.

請使用下列准則來尋找：

- Apache Web伺服器：

   若為具有Apache的Ubuntu,OPcache設定通常位於 `php.ini` 檔案。

   若為具有Apache或nginx的CentOS,OPcache設定通常位於 `/etc/php.d/opcache.ini`

   若未設定，請使用下列命令來找出：

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- 具有PHP-FPM的nginx Web伺服器： `/etc/php/7.2/fpm/php.ini`

如果您有多個 `opcache.ini`，修改所有內容。

## 如何設定PHP選項

要設定PHP選項：

1. 開啟 `php.ini` 在文字編輯器中。
1. 在可用的 [時區設定](https://www.php.net/manual/en/timezones.php)
1. 找到下列設定，並視需要取消註解：

   ```conf
   date.timezone =
   ```

1. 新增您在步驟2找到的時區設定。

1. 變更 `memory_limit` 改為本節開頭建議的值之一。

   例如，

   ```conf
   memory_limit=2G
   ```

1. 新增或更新 `realpath_cache` 設定以符合下列值：

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

1. 儲存您的變更並退出文字編輯器。

1. 開啟另一個 `php.ini` （如果不同），並在其中進行相同的變更。

## 設定OPcache選項

若要設定 `opcache.ini` 選項：

1. 在文本編輯器中開啟OPcache配置檔案：

   - `opcache.ini` (CentOS)
   - `php.ini` （烏本圖）
   - `/etc/php/7.2/fpm/php.ini` (nginx Web伺服器（CentOS或Ubuntu）)

1. 找出 `opcache.save_comments` 並在必要時取消註解。
1. 請確定其值設為 `1`.
1. 儲存您的變更並退出文字編輯器。
1. 重新啟動Web伺服器：

   - 阿帕奇、烏本圖： `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu和CentOS: `service nginx restart`

## 疑難排解

請參閱下列Adobe Commerce支援文章，以取得疑難排解PHP問題的協助：

- [在瀏覽器中存取Adobe Commerce時發生PHP版本錯誤或404錯誤](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP設定錯誤](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [未正確安裝PHP mcrypt擴展](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本就緒性檢查問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [常見PHP致命錯誤和解決方案](https://support.magento.com/hc/en-us/articles/360030568432)
