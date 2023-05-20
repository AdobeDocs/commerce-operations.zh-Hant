---
title: 系統要求
description: 使用此參考可確定已與Adobe Commerce和Magento Open Source版本一起測試的所需軟體依賴項。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# 系統要求

下表顯示了Adobe已通過特定Adobe Commerce和Magento Open Source版本測試的第三方軟體依賴項的版本。 Adobe僅支援下表中所述的系統要求組合。

例如，2.4.5已通過MariaDB 10.4進行完全測試。Adobe建議在升級到2.4.5之前先升級到MariaDB 10.4。

{{$include /help/_includes/templated/system-requirements-table.md}}

## 雜項

本節介紹所有其他類型必需軟體和可選軟體的支援和相容性。

>[!NOTE]
>
>以下要求適用於Adobe Commerce和Magento Open Source的最新2.4.x修補程式版本。

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器

### 作業系統(Linux x86-64)

Linux發行版，如RedHat Enterprise Linux(RHEL)、CentOS、Ubuntu、Debian等。 MicrosoftWindows和macOS不受支援。

### PHP擴展

>[!NOTE]
>
>的 [PHP安裝說明](prerequisites/php-settings.md) 包括安裝這些擴展的步驟。

{{$include /help/_includes/templated/php-extensions.md}}

請參閱 [正式PHP文檔](https://php.net/manual/en/extensions.php) 的子菜單。

### PHP OPcache

強烈建議您驗證 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 因效能原因啟用。 OPcache在許多PHP分發中啟用。 要驗證是否已安裝，請參閱 [PHP文檔](prerequisites/php-settings.md)。

如果必須單獨安裝，請參閱 [PHP OPcache文檔](https://php.net/manual/en/opcache.setup.php)。

### PHP設定

我們建議使用特定的PHP配置設定，如 `memory_limit`這樣可以避免使用Adobe Commerce和Magento Open Source時的常見問題。

有關詳細資訊，請參見 [所需的PHP設定](prerequisites/php-settings.md)。

### PHPUnit

PHPUnit（作為命令行工具）9.0.0

### RAM

升級您從Commerce Marketplace和其他源獲取的應用程式和擴展最多需要2 GB的RAM。 如果您使用的系統的RAM小於2 GB，建議您建立 [交換檔案](https://support.magento.com/hc/en-us/articles/360032980432);否則，升級可能會失敗。

### 系統依賴項

Adobe Commerce和Magento Open Source需要以下系統工具來執行某些操作：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS需要有效的安全證書。
- 不支援自簽名SSL證書。
- 傳輸層安全性(TLS)要求 — PayPal和 `repo.magento.com` 都需要TLS 1.2或更高版本。

### 支援的瀏覽器

店面和管理員：

- Microsoft邊緣（最新版和舊版）
- 火狐(最新和以前的主要版本；任何作業系統)
- Chrome(最新和以前的主要版本；任何作業系統)
- Safari(最新和以前的主要版本；僅macOS)
- 用於iPad2、iPadMini、iPad的Safari Mobile，帶Retina Display(iOS12或更高版本)，用於案頭店面
- iPhone6號或更高版本的Safari Mobile;iOS12或更高版本，用於移動店面
- 移動版（最新版和舊版主版） [Android 4或更高版本] )

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 或更晚（僅限開發環境）;會對效能產生不利影響)

>[!NOTE]
>
>已知問題 `xdebug` 可能影響Adobe Commerce或Magento Open Source安裝，或在安裝後訪問店面或管理員。 有關詳細資訊，請參閱 [xdebug的已知問題](https://support.magento.com/hc/en-us/articles/360034242212)。
