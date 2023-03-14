---
title: 平台工具
description: 選擇您Adobe Commerce實作的建議平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

必須仔細思考並嚴格測試哪些方面，以確保電子商務網站在不受干擾的情況下運行。 您不僅必須確定適當的解決方案來處理站點的各個方面（從資料儲存和寫程式到快取和安全性），而且還需要適當的流程來確保平台的交付，該平台運行順暢，而且可以高效地構建和優化。

本節不僅提供多種Adobe Commerce實作中經過測試和完善的工具、解決方案、流程和方法，也提供我們的建議，讓解決方案最符合特定的業務需求和目標。

下表包含我們建議的解決方案，可在Adobe Commerce內使用這些解決方案來提升平台的效能：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 資料庫 | MySQL、MariaDB、Percona |
| 寫程式語言 | PHP, JS,HTML，更少CSS |
| 整合開發環境(IDE) | Eclipse、PHPStorm |
| Web伺服器 | Nginx、Apache |
| 快取服務 | 紅，清漆 |
| 搜尋服務 | Elasticsearch |
| 消息隊列服務 | [!DNL RabbitMQ] |
| 安全掃描工具 | 聲納庫比、扎普 |

## 資料庫

我們根據品牌需求使用三種不同的工具。 如果您不希望您的儲存處理極端負載， MySQL就像Adobe Commerce資料庫一樣是絕佳的基準解決方案。

MariaDB更注重社群，對於更關心功能而非純粹效能的用戶，其工作效果更好。 MariaDB支援大量資料庫引擎、磁碟加密、複雜的水準互連和擴展功能，這對於大型Adobe Commerce商店來說可能很有趣。

Percona是MySQL的一個分支，它以效能和峰值負載處理為中心。 如果您需要更優質的生活和DevOps功能，請選擇MariaDB。 如果您的目標是在大型資料集中取得高負載效能，請前往Percona 。

## 寫程式語言

Adobe Commerce是基於PHP的應用程式，最新版本始終與最新穩定的PHP版本相容(例如，Adobe Commerce 2.4版建議使用PHP 7.4)。 為了獲得更高的安全性和效能，在配置PHP時要考慮幾個因素，以便在請求處理時獲得最大的速度和效率。 Adobe Commerce Web店面是以HTML、JavaScript和LESS CSS前置處理器建置而成。

## Web伺服器

Adobe Commerce完全支援Nginx和Apache Web伺服器。 Adobe Commerce提供兩者的範例建議組態檔：

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx示例包含用於提高效能的設定，並且設計為無需重新配置。

## 快取服務

Adobe Commerce提供許多儲存快取和會話資料的選項，包括Redis、Memcache、檔案系統和資料庫。 對於具有多個Web節點的設定，Redis是最佳選項。

強烈建議使用清漆作為您商店的整頁快取伺服器。 Adobe Commerce會為清漆分發包含所有效能建議設定的範例組態檔。

## 搜尋服務

對於Adobe Commerce 2.4版和更新版本，所有安裝都必須設定為使用Elasticsearch或OpenSearch作為目錄搜尋解決方案。 Elasticsearch提供目錄中產品的快速進階搜尋。 Elasticsearch適用於2.4之前的版本，但建議使用。

## 消息隊列服務

消息隊列提供非同步通信機制，其中消息的發送者和接收者不相互聯繫。 [!DNL RabbitMQ] 是開放源碼消息代理程式，提供可靠、高可用、可擴展和便攜的消息傳送系統。

## 安全工具

此 [Adobe Commerce安全掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 可讓您定期監控您的商店網站，並接收已知安全風險、惡意軟體和過時軟體的更新。 通常，您會在開始進行使用者接受測試(UAT)時開始使用此工具。 除了Adobe Commerce安全性掃描工具(此工具可供所有實作和Adobe Commerce版本使用)之外，CI/CD程式期間和每次發行前也可使用其他選項。

SonarQube是開放原始碼的品質管理平台，旨在分析和評估程式碼的技術品質。 SonarQube不僅提供程式碼錯誤、語法錯誤和弱點的完整報告，也提供修正程式碼的建議和範例。 SonarQube是在CI/CD環境中使用的理想工具，它能夠在部署前分析代碼。

Zed Attack Proxy(ZAP)是一種免費的安全測試工具，被全球成千上萬的筆測試者使用。 ZAP由OWASP開發，是最常用的手動安全測試工具之一。
