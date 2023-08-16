---
title: 平台工具
description: 選擇建議的Adobe Commerce實作平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

為了維持電子商務網站不受干擾地運作，必須深入思考並嚴格測試各方面。 您不僅必須找出正確的解決方案來處理網站的各個層面（從資料儲存和程式設計，到快取和安全性），而且還需要正確的程式來確保交付的平台既順暢執行又能有效建置和最佳化。

本節不僅提供在多個Adobe Commerce實作中經過測試和完善的工具、解決方案、流程和方法，也提供我們對於哪些解決方案最符合特定業務需求和目標的建議。

下表包含我們建議的解決方案，且可用於Adobe Commerce中以提升平台效能：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 資料庫 | MySQL、MariaDB、Percona |
| 程式語言 | PHP、JS、HTML，較少CSS |
| 整合式開發環境(IDE) | Eclipse， PHPStorm |
| 網頁伺服器 | Nginx、Apache |
| 快取服務 | 紅葡萄酒，亮漆 |
| 搜尋服務 | Elasticsearch |
| 訊息佇列服務 | [!DNL RabbitMQ] |
| 安全性掃描工具 | SonarQube， ZAP |

## 資料庫

我們根據品牌需求來使用三種不同的工具。 如果您不希望存放區處理極端負載，MySQL是做為Adobe Commerce資料庫的絕佳基準解決方案。

MariaDB更加以社群為中心，對於更關注功能而非單純效能的使用者而言效果更佳。 MariaDB支援大量資料庫引擎、磁碟加密、複雜的水準互連，以及擴充功能，這些對於大型Adobe Commerce商店來說很有趣。

Percona是MySQL的一個分支，以效能和尖峰負載處理為中心。 如果您需要更多生活品質和DevOps功能，請選擇MariaDB。 如果您的目標是在大型資料集中獲得高負載效能，請改用Percona。

## 程式語言

Adobe Commerce是以PHP為基礎的應用程式，且最新發行版本一律與最新穩定PHP版本相容(例如，Adobe Commerce 2.4版建議使用PHP 7.4)。 為了獲得更高的安全性和效能，在設定PHP以取得請求處理的最大速度和效率時，需要考慮幾個因素。 Adobe Commerce網站店面是以HTML、JavaScript和LESS CSS前置處理器建置而成。

## Web伺服器

Adobe Commerce完全支援Nginx和Apache網頁伺服器。 Adobe Commerce提供兩種情況的建議設定檔範例：

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx範例包含改善效能的設定，因此不需要重新配置。

## 快取服務

Adobe Commerce提供多種選項來儲存您的快取和工作階段資料，包括Redis、Memcache、檔案系統和資料庫。 若是含有多個網頁節點的設定，Redis是最佳選項。

我們強烈建議您使用Varnish做為商店的整頁快取伺服器。 Adobe Commerce會散發Varnish的設定檔範例，其中包含所有建議的效能設定。

## 搜尋服務

對於Adobe Commerce 2.4版和更新版本，所有安裝都必須設定為使用Elasticsearch或OpenSearch作為目錄搜尋解決方案。 Elasticsearch提供對目錄中產品的快速和進階搜尋。 2.4之前的版本可選擇使用Elasticsearch，但建議使用。

## 訊息佇列服務

訊息佇列提供非同步通訊機制，讓訊息的傳送者與接收者不會相互聯絡。 [!DNL RabbitMQ] 是開放原始碼的訊息代理人，提供可靠、高可用性、可擴充且可攜式訊息系統。

## 安全性工具

此 [Adobe Commerce安全性掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 可讓您定期監視商店網站，並接收已知安全性風險、惡意程式碼和過時軟體的更新。 通常，當您開始使用者驗收測試(UAT)時，就會開始使用此工具。 Adobe Commerce安全性掃描工具是免費的，適用於Adobe Commerce的所有實作和版本，除此之外，還有其他選項可以在CI/CD流程期間和每個版本之前使用。

SonarQube是開放原始碼品質管理平台，專為分析和測量程式碼的技術品質而設計。 SonarQube不僅提供完整的程式碼錯誤、語法錯誤和弱點報告，也提供修正程式碼的建議與範例。 SonarQube非常適合用於CI/CD環境，作為能夠在部署前分析程式碼的工具。

Zed Attack Proxy (ZAP)是免費的安全性測試工具，全球數千筆測試者都會使用。 ZAP由OWASP開發，是手動安全性測試最常用的工具之一。
