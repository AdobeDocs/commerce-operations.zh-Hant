---
title: 最佳化後端效能
description: 瞭解如何最佳化Adobe Commerce網站的後端效能。
badge: label="貢獻者： objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: e5df5a7242dbe8ceff548257daeb39f7c9fc5c69
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# 最佳化後端效能的最佳實務

本主題概述調查及最佳化Adobe Commerce網站後端效能的最佳實務，並專注於資料庫最佳化和測試。 開發人員可使用此資訊來調查每個Commerce專案的獨特內容，並找出將後端設定和作業最佳化，以改善網站效能的機會。

>[!NOTE]
>
>Recommendations和範例的靈感源自於在真實世界的使用者端參與中遵循的objectsource流程，以大規模提供高效能的Adobe Commerce網站。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 最佳化資料庫以提高效能

資料庫最佳化是提升使用者體驗及增加銷售量的有效方式。 資料庫是Commerce網站的骨幹，當您最佳化資料庫時，可以防止網站效能緩慢，並免除冗長的載入時間，進而造成客戶的不便。

### 壓力測試

高流量期間（例如黑色星期五）要求Commerce網站處理大量流量。 為了準備此類事件，壓力測試對於瞭解網站在指數負載增加下的運作方式至關重要。

GTmetrix是一種可用於壓力測試的工具。 設定GTmetrix來復寫並乘以正常的訪客行為和動作，以增加量測網站負載整備程度。 然後，執行測試以識別並解決在主要購物事件期間可能影響效能和網站可用性的問題。

進一步瞭解如何為高流量期間準備Commerce專案：

- [假日整備](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [假日購物分析](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [突波容量增加](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### 載入測試

您也可以使用GTmetrix或類似的工具，以載入測試Commerce專案。 作為壓力測試的前驅，負載測試對於大型高流量網站而言是必不可少的做法。 預測並緩解尖峰負載下影響網站效能的問題，避免意外的網站中斷、客戶挫敗及財務損失。

使用GTmetrix來模擬大量流量，並分析網站效能，以取得有關網站容量的明確資訊。 這項分析可協助您找出並解決瓶頸問題，找出最佳化機會，確保Commerce網站在負載增加的情況下仍能有效運作。

進一步瞭解測試Adobe Commerce專案：

- [測試指引](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) （雲端基礎結構）
- [應用程式測試](https://developer.adobe.com/commerce/testing/guide/)

### 識別並解決效能問題

使用New Relic和Adobe Commerce的Observation等各種工具來偵測瓶頸並有效最佳化Commerce網站，進而解決效能問題。 雲端基礎結構上的Adobe Commerce包含[New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)，而且雲端和內部部署都包含Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)的[觀察。

使用這些工具來分析網站效能，並找出與下列相關之效能問題：

- CPU密集功能
- 查詢和後端操作的快取管理設定
- 協力廠商API呼叫
- Cron排程

例如，您可以仔細檢查以產品詳細資料和類別頁面為焦點的交易。 找出可最佳化以改進效能的耗時流程。 在一個使用者端參與中，objectsource注意到產品詳細資料頁面上出現效能問題，並發現API呼叫耗用3.5%的效能時間。 他們根據此結果，檢查程式碼執行的階層，以查明並修正造成瓶頸的問題。

進一步瞭解管理網站效能：

- [效能監視](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) （雲端基礎結構）
- [效能最佳化審查](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [設定最佳實務](/help/performance/configuration.md)
- [Adobe Commerce的觀察結果](/help/tools/observation-for-adobe-commerce/intro.md)

### 最佳化MySQL效能

透過實作資料庫叢集和查詢最佳化來解決MySQL效能問題，是改善高流量期間（例如Black Friday）之前和期間效能的有效方法。

#### 實作資料庫叢集

高流量的網站經常會遇到資料庫瓶頸，主要原因是依賴單一MySQL伺服器。 您可以實作資料庫叢集化來解決這些瓶頸問題，這是一種可改善效能並確保高可用性的分散式架構。

資料庫叢集可讓多個Web節點連線至多個MySQL伺服器，將尖峰流量期間與資料庫相關問題的影響降到最低。 使用Galera Cluster之類的工具，為Commerce網站設定資料庫叢集。 Galera叢集包含在雲端基礎結構](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html)上部署的[個Adobe Commerce專案。

#### 最佳化MySQL查詢

通常，大部分Adobe Commerce網站的基礎架構是由連線到單一MySQL伺服器的多個Web節點所組成。

在此設定中，每個前端Web節點都會連線至Galera叢集，以允許使用多個MySQL伺服器。 增加前端Web節點的數目可以改善應用程式效能，但單一MySQL伺服器仍是一個瓶頸。

若要最佳化MySQL伺服器效能並最小化瓶頸，必須識別並減少不必要的查詢。 例如，如果您每秒傳送1,000個查詢，但僅需要200個，最佳化和減少查詢計數可以顯著改善效能。

進一步瞭解設定和最佳化MySQL：

- [資料庫組態的最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- Galera DB復寫的[緩慢復寫](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [一般MySQL准則](/help/installation/prerequisites/database/mysql.md)
- [MySQL查詢快取](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## 有效管理cron工作：效能與時間

Cron工作在處理網站背景工作（例如產生報表和編制產品索引）時扮演重要角色。 但是，cron工作最佳化需要仔細考慮其對整體效能的影響。 開發人員必須評估排程頻率，並根據特定需求決定最佳時機。

為了平衡效能與便利性，通常建議在低流量期間排程cron工作。 然而，與不同時區的客戶打交道可能會帶來挑戰，需要深思熟慮的方法，以確保跨多個地理位置的和諧體驗。

如果您負責最佳化cron效能和時間，請檢閱Commerce管理員目前的cron設定，並瞭解如何為Commerce專案設定和設定cron工作。

此外，您可以使用Adobe Commerce的觀察來檢視cron相關的績效指標。 此工具結合來自多個來源的記錄資料，協助您更好地管理Adobe Commerce網站效能並診斷問題。

進一步瞭解Adobe Commerce cron實作：

- _Commerce系統管理使用手冊_&#x200B;中的[Cron （排程工作）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html)
- [應用程式設定 — crons屬性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （雲端基礎結構）
- [設定並執行crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （內部部署）
- Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)的[觀察結果（請參閱[!UICONTROL Cron]和[!UICONTROL MySQL]標籤）。
