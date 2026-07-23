---
title: 系統需求
description: 瞭解Adobe Commerce的軟體相依性和系統需求。 檢視經過測試的設定，瞭解與部署環境的相容性。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# 系統需求

下列資訊摘要說明針對Adobe Commerce測試的軟體相依性和服務。

雲端上Commerce的相依性存在某些差異。 雲端上Adobe Commerce的服務版本和相容性支援，取決於測試並部署至託管雲端環境的服務，有時與Adobe Commerce內部部署支援的版本不同。

>[!IMPORTANT]
>
>系統需求表會列出這些套用的Adobe Commerce版本，包括標示為測試版或搶先存取的版本。
>如需最新發佈的Commerce版本，請參閱[發行說明](../release/release-notes/overview.md)。
>
>當您的服務版本不符合您Commerce版本的支援設定時，行為可能與Adobe在測試中可以重現的行為不同。 Adobe支援可能會要求您在調查、疑難排解或驗證回報的行為之前，讓環境與支援的設定保持一致。 調整環境後，Adobe支援可繼續調查。

下表顯示Adobe已使用特定Adobe Commerce發行版本測試的協力廠商軟體相依性版本。

Adobe僅支援下表所列的系統需求組合。 Adobe不會驗證或支援不符合所列組合的設定。 例如，Adobe Commerce 2.4.9會透過MariaDB 12.3進行測試。 請先升級至MariaDB 12.3，再升級至2.4.9。

## 最新Commerce發行版本的系統需求

下表概述所有受支援Commerce版本最新版本的系統需求。 Adobe建議所有客戶升級至這些版本。

>[!BEGINTABS]

>雲端上的[!TAB Commerce]

雲端上的[Commerce範本](https://github.com/magento/magento-cloud)針對與每個發行版本的最新Commerce版本相容的服務，提供預設設定。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

針對預設組態，服務與版本定義於[的`services.yaml`檔案](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)。
如需詳細資訊，請參閱*雲端基礎結構上的Commerce*&#x200B;指南中的[設定服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0已於2026年4月30日停止支援(EOS)。**
在此日期之後，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4將不提供相容性或
支援在MySQL 8.0之後發行的任何MySQL版本。Adobe不會
在此Adobe上驗證或支援較新的MySQL主要版本
Commerce版本行。
執行2.4.7、2.4.6、2.4.5、2.4.4版的所有Adobe Commerce內部部署客戶為
建議將其資料庫伺服器移轉至相容的MariaDB版本。

雲端上的Adobe Commerce客戶必須在支援的版本上維持平台相依性。 請參閱生命週期原則中的[平台相依性](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17於2026年1月15日終止支援(EOS)。**
在此日期之後，Adobe Commerce 2.4.6、2.4.5和2.4.4將不提供相容性或
支援在Elasticsearch 7之後發行的任何Elasticsearch版本。Adobe不會
在此Adobe上驗證或提供對較新Elasticsearch主要版本的支援
Commerce版本行。
執行2.4.6、2.4.5、2.4.4版的所有Adobe Commerce內部部署客戶為
建議將搜尋基礎結構移轉至相容的OpenSearch版本。

>[!ENDTABS]

## 舊版Commerce的系統需求

下表列出Adobe Commerce發行版本的系統需求，包括延伸支援中的系統需求。 這些表格僅供參考。 Adobe不建議使用不支援的軟體相依性版本，而支援需要您先將環境調整為支援的設定，我們才能調查、疑難排解或驗證回報的行為。

>[!NOTE]
>
>Adobe Commerce 2.4.6在[延伸支援](../release/lifecycle-policy.md#extended-support)到&#x200B;**2027年8月30日**&#x200B;之間，接著是[僅限安全性過渡期間](../release/lifecycle-policy.md#security-only-transitional-period)到&#x200B;**2028年5月31日**。 這些布建僅供Adobe Commerce客戶使用。 它們不會擴充對第三方相依性（例如MySQL）的支援。
>
>如果您在雲端上執行Adobe Commerce，則必須在&#x200B;**2028年6月1日** [版本升級強制日期](../release/version-upgrade-enforcement-policy.md)之前升級至支援的版本或移轉至[!DNL Adobe Commerce as a Cloud Service]。 如需完整生命週期日期，請參閱[支援結束日期](../release/lifecycle-policy.md#end-of-support-dates)表格。
>
>表格會收合以將此文章的長度最小化。 選取標題以展開。

+++舊版的需求

>[!BEGINTABS]

>雲端上的[!TAB Commerce]

雲端範本](https://github.com/magento/magento-cloud)上的[Commerce提供與特定Commerce版本相容之服務的預設設定。

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

針對預設組態，服務與版本定義於[的`services.yaml`檔案](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)。
如需詳細資訊，請參閱*雲端基礎結構上的Commerce*&#x200B;指南中的[設定服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0已於2026年4月30日停止支援(EOS)。**
在此日期之後，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4將不提供相容性或
支援在MySQL 8.0之後發行的任何MySQL版本。Adobe不會
在此Adobe上驗證或支援較新的MySQL主要版本
Commerce版本行。
執行2.4.7、2.4.6、2.4.5、2.4.4版的所有Adobe Commerce內部部署客戶為
建議將其資料庫伺服器移轉至相容的MariaDB版本。

雲端上的Adobe Commerce客戶必須在支援的版本上維持平台相依性。 請參閱生命週期原則中的[平台相依性](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17於2026年1月15日終止支援(EOS)。**
在此日期之後，Adobe Commerce 2.4.6、2.4.5和2.4.4將不提供相容性或
支援在Elasticsearch 7之後發行的任何Elasticsearch版本。Adobe不會
在此Adobe上驗證或提供對較新Elasticsearch主要版本的支援
Commerce版本行。
執行2.4.6、2.4.5、2.4.4版的所有Adobe Commerce內部部署客戶為
建議將搜尋基礎結構移轉至相容的OpenSearch版本。

>[!ENDTABS]

+++

## PHP設定

有特定的PHP組態設定，例如`memory_limit`設定，可協助您在使用Adobe Commerce時避免常見問題。 請參閱[必要的PHP設定](prerequisites/php-settings.md)。

如需雲端組態指南，請參閱&#x200B;*雲端基礎結構上的Commerce*&#x200B;指南中的[PHP設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)。

### PHP OPcache

Adobe建議您基於效能原因來驗證[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)是否已啟用。 OPcache已在許多PHP分配中啟用。

- **對於雲端基礎結構部署上的Adobe Commerce**，預設會安裝`opcache`擴充功能。
- **對於Adobe Commerce內部部署：**
  - [確認已安裝PHP OPcache延伸模組](prerequisites/php-settings.md#verify-php-is-installed)。
  - 如需效能設定的特定指引，請參閱&#x200B;*效能最佳實務*&#x200B;指南中的[PHP設定](../performance/software.md#php-settings)軟體建議。


如果您必須單獨安裝OPcache，請參閱[PHP OPcache檔案](https://www.php.net/manual/en/opcache.setup.php)。

### PHP程式控制

{{php-process-control}}

### PHPUnit

支援的PHPUnit主要版本取決於Adobe Commerce發行版本。 Adobe使用PHPUnit 12測試2.4.9、使用PHPUnit 10測試2.4.8-p5，以及使用PHPUnit 9測試2.4.7-p10到2.4.4-p18。 在主要版本中安裝PHPUnit作為命令列工具，該版本符合您發行版本的Adobe測試設定。

### PHP擴充功能

[PHP安裝指示](prerequisites/php-settings.md)包含安裝這些擴充功能的步驟。

>[!TIP]
>
>有關雲端基礎結構中的PHP擴充功能，請參閱&#x200B;_雲端基礎結構上的Commerce_&#x200B;指南中的[啟用PHP擴充功能](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)。

>[!BEGINTABS]

>雲端上的[!TAB Commerce]

下表顯示在雲端平台上部署Adobe Commerce時支援的PHP擴充功能。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce內部部署]

{{$include /help/_includes/templated/php-extensions.md}}

如需安裝詳細資訊，請參閱[PHP檔案](https://www.php.net/manual/en/extensions.php)。

>[!ENDTABS]

## 其他軟體需求

本節說明所有其他必要和選用軟體型別的支援與相容性。

>[!NOTE]
>
>下列需求適用於Adobe Commerce的最新2.4.x修補程式版本。 相關時，提供雲端基礎結構上的Commerce指引。

### 瀏覽器

店面和管理：

- Microsoft Edge （最新和先前的主要版本）
- Firefox （任何作業系統上最新和先前的主要版本）
- Chrome （任何作業系統上最新和先前的主要版本）
- Safari （僅限macOS上的最新和先前主要版本）
- 適用於iOS的Safari （店面的最新和先前主要版本）
- 適用於Android的Chrome （店面的最新和先前主要版本）

### 郵件伺服器

郵件傳輸代理(MTA)或SMTP伺服器。 雲端基礎結構上的Commerce使用[SendGrid電子郵件服務](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)。

### 記憶體

升級從Commerce Marketplace和其他來源取得的應用程式和擴充功能，最多可能需要2 GB的RAM。 如果您使用的系統RAM小於2 GB，請建立[交換檔案](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)。 否則，您的升級可能會失敗。

### 作業系統(Linux x86-64)

Linux發行版本，例如Red Hat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

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

如需雲端基礎結構上的Commerce，請參閱&#x200B;*雲端基礎結構上的Commerce*&#x200B;指南中的[Fastly設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)。

### Xdebug

若為Adobe Commerce，請使用[php_xdebug 2.5.x](https://xdebug.org/download)或更新版本（僅限開發環境；可能會對效能造成不良影響）。

如需雲端上的Adobe Commerce，請參閱&#x200B;*雲端基礎結構上的Commerce*&#x200B;指南中的[設定Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)。

>[!NOTE]
>
>`xdebug`有已知問題，可能會影響Adobe Commerce安裝或安裝後對店面或管理員的存取。 檢視&#x200B;_Commerce支援知識庫_&#x200B;中影響`xdebug`安裝](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)的[已知問題。

<!-- Last updated from includes: 2026-07-22 16:57:39 -->

