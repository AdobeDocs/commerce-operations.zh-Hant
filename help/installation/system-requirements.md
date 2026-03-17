---
title: 系統需求
description: 瞭解Adobe Commerce的軟體相依性和系統需求。 探索經過測試的設定，以確保與您的部署環境相容。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 766226dc998aafe54bc84d77cabee6fb0a969e6c
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 系統需求

以下摘要說明針對Adobe Commerce測試的軟體相依性和服務。

雲端上Commerce的相依性存在某些差異。 雲端上Adobe Commerce的服務版本和相容性支援，取決於測試並部署至託管雲端環境的服務，有時與Adobe Commerce內部部署支援的版本不同。 例如，內部部署的Elasticsearch 2.4.4支援Commerce 7.17，但雲端上的Adobe Commerce 2.4.4支援OpenSearch 1。

>[!NOTE]
>
>系統需求表會識別涵蓋的特定Adobe Commerce版本，包括任何明確標示為測試版或搶先存取的版本。 請參閱[發行說明](../release/release-notes/overview.md)以進一步瞭解最新發行版本的Adobe Commerce。

下表顯示Adobe已使用特定Adobe Commerce發行版本測試的協力廠商軟體相依性版本。

Adobe僅支援下表所述的系統需求組合。 例如，2.4.5已透過MariaDB 10.4完成測試。Adobe建議您在升級至2.4.5之前，先升級至MariaDB 10.4。

為了確保順利升級程式並防止部署失敗，Adobe建議您逐步升級RabbitMQ版本。 例如，從版本3.8升級至4.1時，您應該先從3.8升級至3.9，再從3.9升級至3.10，以此類推。 到達版本3.13之後，您才應該繼續升級至版本4.1。

>[!BEGINTABS]

>雲端上的[!TAB Commerce]

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

請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)指南中的&#x200B;*設定服務*。

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP設定

有特定的PHP組態設定，例如`memory_limit`設定，可協助您在使用Adobe Commerce時避免常見問題。 請參閱[必要的PHP設定](prerequisites/php-settings.md)。

如需雲端組態指南，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)指南中的&#x200B;*PHP設定*。

### PHP OPcache

Adobe建議您基於效能原因來驗證[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)是否已啟用。 OPcache已在許多PHP分配中啟用。
- **對於雲端基礎結構部署上的Adobe Commerce**，預設會安裝`opcache`擴充功能。
- **對於Adobe Commerce內部部署：**
   - [確認已安裝PHP OPcache延伸模組](prerequisites/php-settings.md#verify-php-is-installed)。
   - 如需效能設定的特定指引，請參閱[效能最佳實務](../performance/software.md#php-settings)指南中的&#x200B;*PHP設定*&#x200B;軟體建議。


如果您必須單獨安裝OPcache，請參閱[PHP OPcache檔案](https://www.php.net/manual/en/opcache.setup.php)。

### PHP程式控制

{{php-process-control}}

### PHPUnit

PHPUnit v9 （作為命令列工具）。

### PHP擴充功能

[PHP安裝指示](prerequisites/php-settings.md)包含安裝這些擴充功能的步驟。

>[!TIP]
>
>有關雲端基礎結構中的PHP擴充功能，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)指南中的&#x200B;_啟用PHP擴充功能_。

>[!BEGINTABS]

>雲端上的[!TAB Commerce]

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
- Safari （最新和先前的主要版本；僅限macOS）
- iOS適用的Safari （店面適用的最新和先前主要版本）
- 適用於Android的Chrome （店面的最新和先前主要版本）

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器。 雲端基礎結構上的Commerce使用[SendGrid電子郵件服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)。

### 記憶體

升級從Commerce Marketplace和其他來源取得的應用程式和擴充功能，最多可能需要2 GB的RAM。 如果您使用的系統RAM小於2 GB，請建立[交換檔案](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)。 否則，您的升級可能會失敗。

### 作業系統(Linux x86-64)

Linux發行版本，例如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

Microsoft Windows和macOS **不支援**。

Adobe Commerce的某些作業需要下列系統工具：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- HTTPS需要有效的安全性憑證。
- 不支援自我簽署SSL憑證。
- 傳輸層安全性(TLS)需求 — PayPal和`repo.magento.com`都需要TLS 1.2或更新版本。

如需雲端基礎結構上的Commerce，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)指南中的&#x200B;*Fastly設定*。

### Xdebug

若為Adobe Commerce，請使用[php_xdebug 2.5.x](https://xdebug.org/download)或更新版本（僅限開發環境；可能會對效能造成不良影響）。

如需雲端上的Adobe Commerce，請參閱[雲端基礎結構上的Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)指南中的&#x200B;*設定Xdebug*。

>[!NOTE]
>
>`xdebug`有已知問題，可能會影響Adobe Commerce安裝或安裝後對店面或管理員的存取。 檢視[Commerce支援知識庫`xdebug`中影響](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)安裝&#x200B;_的_&#x200B;已知問題。


<!-- Last updated from includes: 2026-03-10 20:36:29 -->
