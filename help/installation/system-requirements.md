---
title: 系統需求
description: 請使用此參考資料來識別已在Adobe Commerce發行版本中測試的所需軟體相依性。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 系統需求

以下摘要說明針對Adobe Commerce測試的軟體相依性和服務。

雲端基礎結構上Commerce的相依性有一些差異。 雲端基礎結構上Adobe Commerce的服務版本和相容性支援取決於測試並部署至託管雲端環境的服務，有時與Adobe Commerce內部部署支援的版本不同。 例如，內部部署的Commerce 2.4.4支援Elasticsearch7.17，但雲端基礎結構上的Commerce 2.4.4支援OpenSearch 1.2。

下表顯示Adobe已使用特定Adobe Commerce發行版本測試的協力廠商軟體相依性版本。

Adobe僅支援下表所述的系統需求組合。 例如，2.4.5已透過MariaDB 10.4完成測試。Adobe建議您在升級至2.4.5之前，先升級至MariaDB 10.4。

>[!BEGINTABS]

>[!TAB 雲端上的商務]

此 [雲端上的Commerce範本](https://github.com/magento/magento-cloud) 提供與特定Commerce版本相容之服務的預設設定。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

服務和版本定義於 [此 `services.yaml` 檔案](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). 以下是雲端基礎結構上Commerce 2.4.6的預設服務設定：

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

另請參閱 [設定服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) 在 _雲端基礎結構上的Commerce_ 指南。

>[!TAB 商務內部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP設定

有特定的PHP組態設定，例如 `memory_limit` 設定，可協助您在使用Adobe Commerce時避免常見問題。 另請參閱 [必要的PHP設定](prerequisites/php-settings.md).

如需雲端設定指南，請參閱 [PHP設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) 在 _雲端基礎結構上的Commerce_ 指南。

### PHP OPcache

建議您確認 [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) 基於效能原因而啟用。 OPcache已在許多PHP分配中啟用。 此 `opcache` 擴充功能預設會安裝在雲端基礎結構的Commerce中。

如需內部部署，請確認PHP OPcache已安裝，請參閱 [PHP設定](prerequisites/php-settings.md). 或如需效能設定的特定指引，請參閱下列軟體建議： [PHP設定](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) 在 _效能最佳實務_ 指南。

如果您必須單獨安裝OPcache，請參閱 [PHP OPcache檔案](https://www.php.net/manual/en/opcache.setup.php).

### PHP程式控制

{{php-process-control}}

### PHPUnit

PHPUnit v9 （作為命令列工具）。

### PHP擴充功能

此 [PHP安裝指示](prerequisites/php-settings.md) 包含安裝這些擴充功能的步驟。

>[!TIP]
>
>如需雲端基礎結構中的PHP擴充功能，請參閱 [啟用PHP擴充功能](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) 在 _雲端基礎結構上的Commerce_ 指南。

>[!BEGINTABS]

>[!TAB 雲端上的商務]

下表顯示在雲端平台上部署Adobe Commerce時支援的PHP擴充功能。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB 商務內部部署]

{{$include /help/_includes/templated/php-extensions.md}}

請參閱 [PHP官方檔案](https://www.php.net/manual/en/extensions.php) 以取得安裝詳細資料。

>[!ENDTABS]

## 其他

本節說明所有其他必要和選用軟體型別的支援與相容性。

>[!NOTE]
>
>下列需求適用於Adobe Commerce的最新2.4.x修補程式版本。 相關時，提供雲端基礎結構上的Commerce指引。

### 瀏覽器

店面和管理：

- Microsoft Edge （最新和先前的主要版本）
- Firefox （最新和先前的主要版本；任何作業系統）
- Chrome （最新和先前的主要版本；任何作業系統）
- Safari (最新和先前的主要版本；僅限macOS)
- iOS適用的Safari （店面適用的最新和先前主要版本）
- Chrome for Android （最新和先前主要版本，適用於店面）

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器。 雲端基礎結構上的Commerce使用 [SendGrid電子郵件服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### 記憶體

升級從Commerce Marketplace和其他來源取得的應用程式和擴充功能，最多可能需要2 GB的RAM。 如果您使用的系統RAM小於2 GB，請建立 [交換檔案](https://support.magento.com/hc/en-us/articles/360032980432)；否則，升級可能會失敗。

### 作業系統(Linux x86-64)

Linux發行版本，例如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。 不支援Microsoft Windows和macOS。

Adobe Commerce的某些作業需要下列系統工具：

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

- HTTPS需要有效的安全性憑證。
- 不支援自我簽署SSL憑證。
- 傳輸層安全性(TLS)需求 — PayPal和 `repo.magento.com` 兩者都需要TLS 1.2或更新版本。

如需雲端基礎結構上的Commerce，請參閱 [Fastly設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 在 _雲端基礎結構上的Commerce_ 指南。

### Xdebug

若為Adobe Commerce，請使用 [php_xdebug 2.5.x](https://xdebug.org/download) 或更新版本（僅限開發環境；可能會對效能造成負面影響）。

如需雲端上的Adobe Commerce，請參閱 [設定Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) 在 _雲端基礎結構上的Commerce_ 指南。

>[!NOTE]
>
>有一個已知問題 `xdebug` 可能會影響Adobe Commerce或Magento Open Source安裝，或安裝後對店面或管理員的存取權。 另請參閱 [影響以下的已知問題 `xdebug` 安裝](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) 在 _Commerce支援知識庫_.
