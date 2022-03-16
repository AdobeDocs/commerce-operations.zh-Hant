---
title: Adobe Commerce效能優化
description: 通過更改某些預設設定，準備您的Adobe Commerce項目將Adobe Experience Manager用作CMS。
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe Commerce效能優化

## Adobe Commerce基礎設施AEM的地理位置

為減少生成頁AEM面時發佈者和Adobe CommerceGraphQL之間的延遲，兩個獨立基礎架構的初始設定應在同一AWS（或Azure）區域內進行。 為兩個雲選擇的地理位置也應最接近大多數客戶群，因此客戶端GraphQL請求可以從地理位置接近的位置向大多數客戶提供服務。

## GraphQL在Adobe Commerce的快取

當用戶的瀏覽器或發AEM布者調用Adobe Commerce的GraphQL時，某些調用將在Rebist中快取。 快取的查詢通常是那些包含非個人資料且不太可能經常更改的查詢。 例如：類別、類別清單和產品。 明確未快取的是那些定期更改的，如果快取可能會對個人資料和站點操作帶來風險，例如cart和customerPaymentTokens等查詢。

GraphQL允許您在一次調用中進行多個查詢。 請注意，如果您甚至指定了一個查詢，而Adobe Commerce沒有將其它許多不可快取的查詢快取，則Adobe Commerce將忽略調用中所有查詢的快取。 開發人員在組合多個查詢時應考慮這一點，以確保不會無意中跳過可快取的查詢。

>[!NOTE]
>
> 有關可快取和不可快取查詢的進一步資訊，請參閱Adobe Commerce [開發者文檔](https://devdocs.magento.com/guides/v2.4/graphql/caching.html)。

## 目錄平面表

不建議對產品和類別使用平面表。 使用此不建議使用的功能可能會導致效能降級和索引問題，因此應通過Adobe Commerce管理員在店面部分禁用平面目錄。 某些第三方模組和定制確實需要平面表才能正常運行 — 建議進行評估以瞭解在選擇使用這些擴展或定制時必須使用平面表所產生的影響和風險。

## 快速起源屏蔽

預設情況下，未啟用「快速原點」屏蔽。 Rebliste的源屏蔽的目的是直接減少到Adobe Commerce源的流量：當收到請求時， Abmistey邊緣位置（或「存在點」/POP）會檢查快取的內容並提供它。 如果未快取，則Shield POP將繼續檢查是否快取在該位置（如果內容以前甚至從另一個全局POP請求過，則將快取）。 最後，如果不快取到Shield POP上，則只能繼續到源伺服器。

可以在您的Adobe Commerce管理員Rebistify配置後端設定中啟用Rebisting屏蔽。 您應選擇離Adobe Commerce資料中心最近的防護位置，以獲得最佳效能。

## 快速影像優化

啟用「Applise」（快速）原點屏蔽後，您還可以激活「Applise」（快速）影像優化程式。 當產品目錄影像儲存在Adobe Commerce時，此服務能夠將所有資源密集型的產品目錄影像轉換處理從Adobe Commerce的源地卸載到Rembity和Off。 對於頁載入時間，最終用戶響應時間也被改進，因為影像在邊緣位置被變換，通過減少返回Adobe Commerce源的請求數來消除延遲。

通過管理中的Rebistify配置中的「啟用深層映像優化」，可以啟用Reabliste Image Optimization，儘管只有在您的源防護系統已激活之後。 有關用於Affeist Image Optimization的配置的更多詳細資訊，請訪問Adobe Commerce [開發者文檔](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html)。

![「Adobe Commerce管理員」中「Abmistey」映像優化設定的螢幕快照](../assets/commerce-at-scale/image-optimization.svg)

## 禁用未使用的模組

如果運行Adobe Commerce無頭服務，則只通過GraphQL端點服務請求，並且沒有從Adobe Commerce直接提供前端儲存頁，則許多模組將變得冗餘且未使用。 通過禁用未使用的模組，您的Adobe Commerce代碼庫變得更小、更簡單，因此可以提高效能。 可以使用作曲家管理Adobe Commerce上禁用模組。 哪些模組可以禁用取決於您站點的要求，因此無法提供建議的清單，因為它將特定於每個客戶對Adobe Commerce的實施。

## MySQL和Redis連接激活

預設情況下，MySQL和Redis Slave連接在雲上的Adobe Commerce不會激活。 這是因為這些設定僅適用於預期負載非常高的客戶。 在激活從連接時，跨可用區(Cross-AZ)延遲會更高，因此此設定實際上會降低雲實例上Adobe Commerce的效能，如果實例只接收常規負載級別。

如果Adobe Commerce實例期望負載極大，則激活MySQL和Redis的主從將通過跨不同節點分配MySQL資料庫或Redis上的負載，從而幫助提高效能。

作為指南，在負載正常的環境中，啟用從屬連接將降低10-15%的效能。 但在負載和流量較大的集群上，效能提升約10-15%。 因此，必須將環境與預期的通信量級別進行載入test，以評估此設定是否對載入下的效能時間有益。

要啟用/禁用mysql和redis的從連接，應編輯 `.magento.env.yaml` 檔案以包括以下內容：

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

對於擴展體系結構（拆分體系結構 — 請參閱下面），不應啟用Redis從連接，因為這將導致出現錯誤。 在拆分體系結構的情況下，建議實現Redis的L2快取。

## 在雲擴展（拆分）架構上移到Adobe Commerce

如果在上述所有配置之後，載入test結果或即時基礎架構效能分析仍表明到Adobe Commerce的載入級別始終高於CPU和其他系統資源，則應考慮向擴展（剝離）體系結構的遷移。

使用標準Pro體系結構，有3個節點，每個節點都包含完整的技術堆棧。 通過轉換為剝離層體系結構，此結構將最少更改為6個節點：其中包括Elasticsearch、MariaDB、Redis等核心服務；另外3個用於處理Web流量，包含phpfpm和NGINX。 分層存在更大的擴展可能性：包含資料庫的核心節點可以垂直縮放；Web節點可以水準和垂直擴展，因此可以根據設定的高負載活動週期的需求和需要額外資源的節點上擴展基礎架構，從而具有很大的靈活性。

如果由於對您的站點的負載期望過高而決定切換到分層體系結構，則應就啟用此功能的步驟與您的客戶成功經理進行討論。
