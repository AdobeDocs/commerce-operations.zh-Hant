---
title: 系統需求
description: 使用此參考資料來識別已透過Adobe Commerce和Magento Open Source版本測試的必要軟體相依性。
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# 系統需求

下表顯示Adobe已透過特定Adobe Commerce和Magento Open Source版本測試的協力廠商軟體相依性版本。 Adobe僅支援下表所述的系統需求組合。

例如，2.4.5已通過MariaDB 10.4的完全測試。Adobe建議您在升級到2.4.5之前升級到MariaDB 10.4。

{{$include /help/_includes/templated/system-requirements-table.md}}

## 其他

本節介紹所有其他必需和可選軟體類型的支援和相容性。

>[!NOTE]
>
>下列要求適用於Adobe Commerce和Magento Open Source的最新2.4.x修補程式版本。

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器

### 作業系統(Linux x86-64)

Linux發佈，例如RedHat Enterprise Linux(RHEL)、CentOS、Ubuntu、Debian等。 Microsoft Windows和macOS不受支援。

### PHP擴充功能

>[!NOTE]
>
>此 [PHP安裝說明](prerequisites/php-settings.md) 納入安裝這些擴充功能的步驟。

{{$include /help/_includes/templated/php-extensions.md}}

請參閱 [官方PHP檔案](https://php.net/manual/en/extensions.php) 以了解安裝詳細資訊。

### PHP OPcache

強烈建議您確認 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 因效能原因而啟用。 在許多PHP分發中啟用了OPcache。 若要確認是否已安裝，請參閱 [PHP文檔](prerequisites/php-settings.md).

如果您必須個別安裝，請參閱 [PHP OPcache文檔](https://php.net/manual/en/opcache.setup.php).

### PHP設定

我們建議使用特定的PHP配置設定，例如 `memory_limit`，可避免使用Adobe Commerce和Magento Open Source時的常見問題。

如需詳細資訊，請參閱 [必需的PHP設定](prerequisites/php-settings.md).

### PHPUnit

PHPUnit（作為命令行工具）9.0.0

### RAM

升級您從Commerce Marketplace和其他源獲取的應用程式和擴展，最多需要2 GB的RAM。 如果您使用的系統的RAM少於2 GB，建議您建立 [交換檔案](https://support.magento.com/hc/en-us/articles/360032980432);否則，您的升級可能會失敗。

### 系統依賴項

Adobe Commerce和Magento Open Source需要下列系統工具才能執行部分作業：

- [bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [好](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [sed](https://www.gnu.org/software/sed/manual/sed.html)
- [焦油](https://linux.die.net/man/1/tar)

### SSL

- 有效 [安全證書](https://glossary.magento.com/security-certificate) 是HTTPS的必要項目。
- 不支援自簽名SSL證書。
- 傳輸層安全性(TLS)需求 — PayPal和 `repo.magento.com` 兩者皆需TLS 1.2或更新版本。

### 受支援的瀏覽器

店面和管理員：

- Microsoft Edge（最新和舊版主要版本）
- Firefox(最新和舊版主要版本；任何作業系統)
- Chrome(最新和舊版主要版本；任何作業系統)
- Safari(最新和舊版主要版本；僅限macOS)
- 適用於iPad 2、iPad Mini、iPad（含Retina顯示器）的Safari Mobile(iOS 12或更新版本)，適用於案頭店面
- 適用於iPhone 6或更新版本的Safari Mobile;iOS 12或更新版本，適用於行動店面
- 行動版Chrome（最新和舊版主要版本） [Android 4或更新版本] （行動店面）

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 或更新版本（僅限開發環境）;會對效能造成負面影響)

>[!NOTE]
>
>有已知問題 `xdebug` 可能會影響Adobe Commerce或Magento Open Source安裝，或在安裝後存取storefront或管理員。 如需詳細資訊，請參閱 [xdebug的已知問題](https://support.magento.com/hc/en-us/articles/360034242212).
