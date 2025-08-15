---
title: PHP設定
description: 按照以下步驟安裝必要的PHP擴充功能，並為Adobe Commerce的內部部署安裝設定必要的PHP設定。
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP設定

本主題討論如何設定必要的PHP選項。

>[!NOTE]
>
>最新版Adobe Commerce至少需要PHP 8.1。如需所有支援的PHP版本，請參閱[系統需求](../system-requirements.md)。

如需雲端組態指南，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=zh-Hant)指南中的&#x200B;_PHP設定_。

## PHP程式控制

{{php-process-control}}

## 驗證是否已安裝PHP

PHP預設會安裝在大多數Linux發行版本上。 本主題假設您已安裝PHP。 要驗證是否已安裝PHP，請在命令列中輸入以下內容：

```bash
php -v
```

如果已安裝PHP，則會顯示類似以下內容的訊息：

```
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

如果未安裝PHP （或需要升級），請按照Linux發行版本的說明進行安裝。

## 驗證已安裝的擴充功能

Adobe Commerce需要特定的PHP擴充功能。 下列清單指定每個Commerce版本的必要擴充功能。 清單會從執行每個版本最新版本的部署中自動產生。

{{$include /help/_includes/templated/php-extensions.md}}

若要驗證已安裝的擴充功能：

1. 列出已安裝的模組。

   ```bash
   php -m
   ```

1. 確認已安裝所有必要的擴充功能。
1. 使用用於安裝PHP的相同工作流程來新增任何缺少的模組。

## 檢查PHP設定

>[!WARNING]
>
>如果您使用PHP 7.4.20，請在`pcre.jit=0`檔案中設定`php.ini`。 這會繞過PHP [錯誤](https://bugs.php.net/bug.php?id=81101)，導致CSS無法載入。

- 設定PHP的系統時區；否則，在安裝期間顯示以下錯誤以及與時間相關的操作（如cron）可能無法運作：

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 設定PHP記憶體限制。

  Adobe建議下列事項：

   - 正在編譯程式碼或部署靜態資產，`1G`
   - 偵錯，`2G`
   - 測試，`~3-4G`

- 將PHP `realpath_cache_size`和`realpath_cache_ttl`的值增加到建議的設定：

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  這些設定可讓PHP程式快取檔案的路徑，而不是在頁面載入時查詢它們。 請參閱PHP檔案中的[效能調整](https://www.php.net/manual/en/ini.core.php)。

- 啟用Adobe Commerce 2.1和更新版本所需的[`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)。

  基於效能考量，Adobe建議啟用[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)。 OPcache已在許多PHP分配中啟用。

  Adobe Commerce 2.1和更新版本使用PHP程式碼註解來產生程式碼。

>[!NOTE]
>
>為避免在安裝和升級期間出現問題，Adobe強烈建議您對PHP命令列配置和PHP Web伺服器外掛程式配置都套用相同的PHP設定。 如需詳細資訊，請參閱下一節。

## 尋找PHP組態檔

本節將討論如何找到更新所需設定所需的組態檔。

### 尋找`php.ini`設定檔

若要尋找網頁伺服器組態，請在網頁瀏覽器中執行[`phpinfo.php`檔案](optional-software.md#create-phpinfophp)，並依下列方式尋找`Loaded Configuration File`：

![PHP資訊頁](../../assets/installation/config_phpini-webserver.png)

若要找到PHP命令列組態，請輸入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果您只有一個`php.ini`檔案，請變更該檔案。 如果您有兩個`php.ini`檔案，請變更&#x200B;*兩個*&#x200B;檔案。 若未這麼做，可能會導致無法預測的效能。

### 尋找OPcache組態設定

PHP OPcache設定通常位於`php.ini`或`opcache.ini`中。 位置可能取決於您的作業系統和PHP版本。 OPcache組態檔可能有`opcache`區段或類似於`opcache.enable`的設定。

請使用下列准則來尋找它：

- Apache Web Server：

  對於具有Apache的Ubuntu，OPcache設定通常位於`php.ini`檔案中。

  對於具有Apache或nginx的CentOS，OPcache設定通常位於`/etc/php.d/opcache.ini`

  如果沒有，請使用下列命令來尋找它：

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- PHP-FPM的nginx Web伺服器： `/etc/php/8.1/fpm/php.ini`

如果您有多個`opcache.ini`，請修改全部。

## 如何設定PHP選項

若要設定PHP選項：

1. 在文字編輯器中開啟`php.ini`。
1. 在可用的[時區設定](https://www.php.net/manual/en/timezones.php)中找到伺服器的時區
1. 找到下列設定，並視需要取消註解：

   ```conf
   date.timezone =
   ```

1. 新增您在步驟2中找到的時區設定。

1. 將`memory_limit`的值變更為本節開頭建議的值之一。

   例如，

   ```conf
   memory_limit=2G
   ```

1. 新增或更新`realpath_cache`設定以符合下列值：

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

1. 儲存變更並退出文字編輯器。

1. 開啟其他`php.ini` （如果它們不同）並在其中進行相同的變更。

## 設定OPcache選項

若要設定`opcache.ini`選項：

1. 在文字編輯器中開啟OPcache設定檔案：

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (nginx網頁伺服器（CentOS或Ubuntu）)

1. 找到`opcache.save_comments`，並視需要取消註解。
1. 請確定它的值設定為`1`。
1. 儲存變更並退出文字編輯器。
1. 重新啟動您的網頁伺服器：

   - Apache， Ubuntu： `service apache2 restart`
   - Apache， CentOS： `service httpd restart`
   - nginx、Ubuntu和CentOS： `service nginx restart`

## 疑難排解

請參閱下列Adobe Commerce支援文章，以取得疑難排解PHP問題的說明：

- 在瀏覽器中存取Adobe Commerce時，[PHP版本錯誤或404錯誤](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP設定錯誤](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP mcrypt延伸未正確安裝](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本整備檢查問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [常見的PHP嚴重錯誤與解決方法](https://support.magento.com/hc/en-us/articles/360030568432)
