---
title: 平台工具
description: 為您的Adobe Commerce實施選擇推薦的平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

要確保電子商務網站不受干擾地運行，必須仔細思考並嚴格測試的方面並不少。 您不僅必須確定適當的解決方案來處理站點的各個方面 — 從資料儲存和寫程式到快取和安全性 — 而且您還需要適當的流程來確保平台的交付，該平台運行順利，而且可以高效地構建和優化。

本部分不僅介紹了在多項Adobe Commerce實施中經過測試和完善的工具、解決方案、流程和方法體系，還介紹了我們的建議，這些解決方案最適合特定的業務需要和目標。

下表包括我們推薦的可在Adobe Commerce內用於推動平台效能的解決方案：

| 目的 | 工具 |
|------------------------------------------|-------------------------|
| 資料庫 | MySQL、MariaDB、Percona |
| 寫程式語言 | PHP、JS、HTML、更少CSS |
| 整合開發環境(IDE) | Eclipse、PHPStorm |
| Web伺服器 | Nginx、Apache |
| 快取服務 | 《雷迪斯，清漆》 |
| 搜索服務 | Elasticsearch |
| 消息隊列服務 | 兔MQ |
| 安全掃描工具 | 聲納隊，ZAP |

## 資料庫

根據品牌需要，我們使用了三種不同的工具。 如果您不希望您的儲存處理極端負載，則MySQL是與Adobe Commerce資料庫一樣的絕佳基線解決方案。

MariaDB更注重社區，對於更關心功能而非純粹效能的用戶來說效果更好。 MariaDB支援大量資料庫引擎、磁碟加密、複雜的水準互連和擴展功能，這對於大型Adobe Commerce商店來說可能非常有意義。

Percona是MySQL的一個分支，它圍繞效能和峰值負載處理為中心。 如果您需要更高的生活質量和DevOps功能，請選擇MariaDB。 如果您的目標是在大規模資料集中獲得高負載效能，請轉到Percona。

## 寫程式語言

Adobe Commerce是基於PHP的應用程式，最新版本始終與最新的穩定PHP版本相容(例如，Adobe Commerce版本2.4建議使用PHP 7.4)。 為獲得更高的安全性和效能，在配置PHP以在請求處理時獲得最大的速度和效率時，需要考慮幾個因素。 Adobe Commerce網站前台採用HTML、JavaScript和LESS CSS預處理器。

## Web伺服器

Adobe Commerce完全支援Nginx和Apache Web伺服器。 Adobe Commerce提供建議的配置檔案示例：

- **恩金**—`<magento_home>/nginx.conf.sample`
- **阿帕奇**—`<magento_home>.htaccess.sample`

Nginx示例包含用於提高效能的設定，並且設計為無需重新配置。

## 快取服務

Adobe Commerce提供了許多儲存快取和會話資料的選項，包括Redis、Memcache、檔案系統和資料庫。 對於具有多個Web節點的設定，Redis是最佳選項。

我們強烈建議將清漆用作您的商店的全頁快取伺服器。 Adobe Commerce為清漆分發了一個示例配置檔案，該檔案包含所有建議的效能設定。

## 搜索服務

對於Adobe Commerce2.4版及更高版本，所有安裝都必須配置為使用Elasticsearch作為目錄搜索解決方案。 Elasticsearch提供對目錄中產品的快速和高級搜索。 對於2.4之前的版本，Elasticsearch是可選的，但建議使用。

## 消息隊列服務

消息隊列提供了一種非同步通信機制，其中消息的發送者和接收者不相互聯繫。 RabbitMQ是一個開源消息代理，提供可靠、高可用、可擴展和便攜的消息傳遞系統。

## 安全工具

的 [Adobe Commerce安全掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 使您能夠定期監視您的商店網站並接收已知安全風險、惡意軟體和過期軟體的更新。 通常，您在開始用戶接受測試(UAT)時就會開始使用此工具。 除了Adobe Commerce安全掃描工具(該工具可免費用於Adobe Commerce的所有實施和版本)之外，在CI/CD過程中和每次發佈之前還可以使用其他選擇。

SonarQube是一個開源質量管理平台，旨在分析和衡量代碼的技術質量。 SonarQube不僅提供了代碼錯誤、語法錯誤和漏洞的完整報告，還提供了修復代碼的建議和示例。 SonarQube在CI/CD環境中是一種非常理想的工具，它能夠在代碼部署之前分析代碼。

Zed Attack Proxy(ZAP)是全球成千上萬的筆式測試人員使用的免費安全測試工具。 ZAP是由OWASP開發的，是人工安全測試中最常用的工具之一。
