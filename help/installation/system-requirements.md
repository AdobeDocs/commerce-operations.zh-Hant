---
title: 系統需求
description: 瞭解Adobe Commerce的軟體相依性和系統需求。 探索經過測試的設定，以確保與您的部署環境相容。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b1a202fde89ab05626194aff010111577ef6993
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# 系統需求

以下摘要說明針對Adobe Commerce測試的軟體相依性和服務。

雲端上Commerce的相依性存在某些差異。 雲端上Adobe Commerce的服務版本和相容性支援，取決於測試並部署至託管雲端環境的服務，有時與Adobe Commerce內部部署支援的版本不同。 例如，內部部署的Elasticsearch 2.4.4支援Commerce 7.17，但雲端上的Adobe Commerce 2.4.4支援OpenSearch 1。

>[!NOTE]
>
>系統需求僅適用於Adobe Commerce的發行版本。 不包括Beta或搶先存取版本。 請參閱[發行說明](../release/release-notes/overview.md)以進一步瞭解Adobe Commerce的最新發行版本。

下表顯示Adobe已使用特定Adobe Commerce發行版本測試的協力廠商軟體相依性版本。

Adobe僅支援下表所述的系統需求組合。 例如，2.4.5已透過MariaDB 10.4完成測試。Adobe建議您在升級至2.4.5之前，先升級至MariaDB 10.4。

為了確保順利升級程式並防止部署失敗，Adobe建議您逐步升級RabbitMQ版本。 例如，從版本3.8升級至4.1時，您應該先從3.8升級至3.9，再從3.9升級至3.10，以此類推。 到達版本3.13之後，您才應該繼續升級至版本4.1。

>[!BEGINTABS]
>[!TAB 雲端上的 Commerce]

雲端範本[上的](https://github.com/magento/magento-cloud)Commerce提供與特定Commerce版本相容之服務的預設設定。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

服務與版本定義於[的`services.yaml`檔案](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)。 以下是雲端基礎結構上Commerce 2.4.6的預設服務設定：

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

請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)指南中的&#x200B;_設定服務_。

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP設定

有特定的PHP組態設定，例如`memory_limit`設定，可協助您在使用Adobe Commerce時避免常見問題。 請參閱[必要的PHP設定](prerequisites/php-settings.md)。

如需雲端組態指南，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html)指南中的&#x200B;_PHP設定_。

### PHP OPcache

建議您確認[PHP OPcache](https://www.php.net/manual/en/intro.opcache.php)已因效能原因啟用。 OPcache已在許多PHP分配中啟用。 `opcache`擴充功能預設會安裝在雲端基礎結構上的Commerce中。

若為內部部署，請確認是否已安裝PHP OPcache，請參閱[PHP設定](prerequisites/php-settings.md)。 如需效能設定的特定指引，請參閱[效能最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings)指南中的&#x200B;_PHP設定_&#x200B;軟體建議。

如果您必須單獨安裝OPcache，請參閱[PHP OPcache檔案](https://www.php.net/manual/en/opcache.setup.php)。

### PHP程式控制

{{php-process-control}}

### PHPUnit

PHPUnit v9 （作為命令列工具）。

### PHP擴充功能

[PHP安裝指示](prerequisites/php-settings.md)包含安裝這些擴充功能的步驟。

>[!TIP]
>
>有關雲端基礎結構中的PHP擴充功能，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions)指南中的&#x200B;_啟用PHP擴充功能_。

>[!BEGINTABS]
>[!TAB 雲端上的 Commerce]

下表顯示在雲端平台上部署Adobe Commerce時支援的PHP擴充功能。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/php-extensions.md}}

如需安裝詳細資訊，請參閱[PHP檔案](https://www.php.net/manual/en/extensions.php)。

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
- 適用於Android的Chrome （店面的最新和先前主要版本）

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器。 雲端基礎結構上的Commerce使用[SendGrid電子郵件服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)。

### 記憶體

升級從Commerce Marketplace和其他來源取得的應用程式和擴充功能，最多可能需要2 GB的RAM。 如果您使用的系統記憶體小於2 GB，請建立[交換檔案](https://support.magento.com/hc/en-us/articles/360032980432)；否則，您的升級可能會失敗。

### 作業系統(Linux x86-64)

Linux發行版本，例如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

Microsoft Windows和macOS **不支援**。

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
- 傳輸層安全性(TLS)需求 — PayPal和`repo.magento.com`都需要TLS 1.2或更新版本。

如需雲端基礎結構上的Commerce，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)指南中的&#x200B;_Fastly設定_。

### Xdebug

若為Adobe Commerce，請使用[php_xdebug 2.5.x](https://xdebug.org/download)或更新版本（僅限開發環境；可能會對效能造成不良影響）。

如需雲端上的Adobe Commerce，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html)指南中的&#x200B;_設定Xdebug_。

>[!NOTE]
>
>`xdebug`有已知問題，可能會影響Adobe Commerce安裝或安裝後對店面或管理員的存取。 檢視[Commerce支援知識庫`xdebug`中影響](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html)安裝&#x200B;_的_&#x200B;已知問題。


<!-- Last updated from includes: 2025-10-09 19:48:53 -->
