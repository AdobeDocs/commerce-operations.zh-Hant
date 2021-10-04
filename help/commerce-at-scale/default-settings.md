---
title: Adobe商務效能最佳化
description: 變更部分預設設定，以準備您的Adobe商務專案以使用Adobe Experience Manager作為CMS。
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe商務效能最佳化

## AEM和Adobe商務基礎架構的地理位置

為了在建立頁面時減少AEM發佈商與AdobeCommerce GraphQL之間的延遲，應在相同的AWS（或Azure）區域內托管兩個獨立基礎架構的初始設定。 為這兩種雲選擇的地理位置也應最接近您的大多數客戶，這樣客戶端GraphQL請求就可以從地理位置上非常接近您的大多數客戶。

## GraphQL在Adobe商務中的快取

當使用者的瀏覽器或AEM發佈商呼叫Adobe商務的GraphQL時，系統會快取某些呼叫
很快。 快取的查詢通常是包含非個人資料且不太可能經常變更的查詢。 例如：類別、類別清單和產品。 未明確快取的是定期變更的，而且如果快取，可能會對個人資料和網站操作（例如cart和customerPaymentToken）造成風險。

GraphQL可讓您在單一呼叫中提出多個查詢。 請務必注意，如果您指定甚至一個查詢，Adobe商務不會快取其他許多無法快取的查詢，Adobe商務會略過呼叫中所有查詢的快取。 開發人員在結合多個查詢時應考量這一點，以確保可能不會無意中略過可快取的查詢。

>[!NOTE]
>
> 有關可快取和不可快取查詢的詳細資訊，請參閱Adobe商務[開發人員檔案](https://devdocs.magento.com/guides/v2.4/graphql/caching.html)。

## 目錄平台

不建議對產品和類別使用平面表。 使用此已棄用的功能可能會導致效能降級和索引問題，因此，應該透過店面區段的「Adobe商務管理員」停用平面目錄。 某些協力廠商模組和自訂功能確實需要平面表格才能正常運作，建議您進行評估，以了解在選擇使用這些擴充功能或自訂功能時，必須使用平面表格的相關影響和風險。

## 快源屏蔽

預設情況下，不會啟用「Ampley origin屏蔽」。 Emply的起源屏蔽的目的是直接減少對Adobe商源的流量：收到請求時，Amplyededge位置（或「存在點」/POP）會檢查快取內容並提供它。 如果未快取，則Shield POP會繼續檢查是否快取了該內容（如果先前已從其他全局POP請求內容，則將快取該內容）。 最後，如果未快取Shield POP，則只會繼續到源伺服器。

可在您的AdobeCommerce Admin Abmetly配置後端設定中啟用Origin屏蔽。 為獲得最佳效能，您應選擇最靠近Adobe商務源資料中心的防護位置。

## 快速影像優化

啟用「Ampley Origin屏蔽」後，您就可以激活「Ampley Image Optimizer」。 當產品目錄影像儲存在Adobe商務中時，此服務可讓您從Adobe商務來源將所有耗用大量資源的產品目錄影像轉換處理，以快速和離開方式進行。 隨著影像在邊緣位置進行轉換，減少返回Adobe商務來源的請求數，消除延遲，最終用戶響應時間也得到改善。

在「管理」中，「快速」配置中的「啟用深層影像優化」可以啟用「快速影像優化」，但此操作僅在激活源防護板後進行。 有關「Ampley Image Optimization」配置的詳細資訊，請參閱Adobe商務[開發人員文檔](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html)。

![「Adobe商務管理員」中「快速」影像最佳化設定的螢幕截圖](../assets/commerce-at-scale/image-optimization.svg)

## 禁用未使用的模組

如果執行Adobe商務無周邊，則只會透過GraphQL端點提供請求，而不會直接從Adobe商務提供前端存放區頁面，因此許多模組會變得多餘而未使用。 停用未使用的模組後，您的Adobe商務程式碼庫會變得更小、更簡單，因此可提供效能改善。 可使用撰寫器來管理Adobe商務上的停用模組。 哪些可停用的模組取決於您網站的需求，因此無法提供建議的清單，因為這是每個Adobe商務實作的專屬清單。

## MySQL和Redis連接激活

預設情況下，MySQL和Redis從連接不會在雲上的Adobe商務中激活。 這是因為這些設定僅適用於預期負載非常高的客戶。 從連接激活後，跨可用區(Cross-AZ,Cross-Availability Zones)延遲較高，因此，如果實例僅接收常規載入級別，此設定實際上會降低雲實例上Adobe商務的效能。

如果AdobeCommerce實例預期的負載極大，則激活MySQL和Redis的主從將負載分散到不同節點上，從而有助於提高效能。

作為指南，在負載正常的環境中啟用從連接將使效能降低10-15%。 但在負載和流量較重的叢集上，效能提升約10-15%。 因此，必須以預期的流量級別載入測試您的環境，以評估此設定是否對負載下的效能時間有益。

要啟用/禁用mysql和redis的從連接，應編輯`.magento.env.yaml`檔案以包括以下內容：

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

對於縮放式架構（分割式架構 — 請參閱下方），不應啟用Redis從連線，因為這會導致錯誤出現。 若是分割架構，建議改為為Redis實作L2快取。

## 在雲端縮放（分割）架構上移至Adobe商務

如果在上述所有配置之後，負載測試結果或對即時基礎架構效能的分析仍表明Adobe商務的負載級別始終最大化CPU和其他系統資源，則應考慮到向擴展（拆分）體系結構的遷移。

使用標準的Pro架構，有3個節點，每個節點都包含完整的技術堆疊。 通過轉換為分層體系結構，這將至少更改為6個節點：其中包括Elasticsearch、MariaDB、Redis等核心服務；處理Web流量的其他3個包含phpfpm和NGINX。 分層擴展的可能性更大：包含資料庫的核心節點可以垂直縮放；Web節點可以橫向和縱向擴展，因此可以根據設定的高負載活動週期的需求，在需要額外資源的節點上擴展基礎架構，從而提供大量靈活性。

如果由於對網站的負載期望過高而決定切換至分層架構，則應與您的客戶成功經理討論啟用此功能的步驟。
