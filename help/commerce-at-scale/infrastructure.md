---
title: Adobe Commerce與Adobe Experience Manager基礎架構校準
description: 讓您的Adobe Commerce和Adobe Experience Manager基礎架構保持一致，以設定可接受的逾時和連線限制。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# 基礎架構對齊（逾時和連線限制）

有些具有AEM和Adobe Commerce的設定以及周邊基礎架構（例如負載平衡器）需要校準，而這些設定與連線限制和逾時設定有關。

這些限制之間的未對齊可能表示連線最終在AEM端受到節流，而Adobe Commerce能夠處理更多連線。 同樣地，對於逾時設定，未對齊可能表示逾時錯誤發生在AEM端，而Adobe Commerce仍在處理請求。

針對逾時設定，應檢閱設定並對齊，以防止在載入下出現503逾時錯誤。 有幾個基礎架構和應用程式逾時設定需要檢閱：

![描述AEM逾時和連線限制的編號圖表](../assets/commerce-at-scale/timeout-settings.svg)

## AEM負載平衡器

假設基礎結構中有一個AWS應用程式負載平衡器以及多個Dispatcher/發佈者 — 對於負載平衡器，應考量下列設定：

1. 應檢閱發佈者健康情況檢查，以防止Dispatcher因載入激增而過早退出服務。 負載平衡器健康情況檢查的逾時設定應與發行者逾時設定一致。

   ![顯示AEM負載平衡器健康情況檢查的熒幕擷圖](../assets/commerce-at-scale/health-checks.png)

1. 可以停用Dispatcher目標群組粘著度，也可以使用Round Robin負載平衡演演算法。 這是假設沒有使用的AEM特定功能或AEM使用者工作階段需要設定工作階段粘著度。 並假設使用者登入和工作階段管理僅透過GraphQL在Adobe Commerce上進行。

   ![顯示AEM工作階段粘著度屬性的熒幕擷圖](../assets/commerce-at-scale/session-stickiness.png)

1. 請注意，如果您啟用工作階段粘著性，這可能會導致Fastly請求不會快取，因為依預設，Fastly不會使用Set-Cookies標頭快取頁面。 Adobe Commerce甚至會在可快取頁面(TTL > 0)上設定Cookie，但預設Fastly VCL會移除可快取頁面上的這些Cookie，以便Fastly快取能夠運作。 如果頁面沒有快取，請檢查您可能使用的任何自訂Cookie，同時上傳Fastly VCL並重新檢查網站。

## Dispatcher逾時設定

Dispatcher的「renders」選項中的/timeout可指定存取AEM發佈執行個體的連線逾時時間（毫秒）。 應檢閱此設定，並在出現個別負載平衡器以處理逾時設定時，使用預設設定「0」（無限逾時）。

如果基礎結構中沒有負載平衡器，則應該在Dispatcher /timeout設定中指定逾時設定，並使用符合發佈者中GraphQL逾時設定的值。

## 發佈者

Publisher GraphQL連線限制和逾時：最初，Adobe Commerce CIF GraphQL Client Configuration Factory OSGI設定中的「最大HTTP連線」應設定為預設的「Fastly最大連線限制」，目前設定為200。 即使AEM陣列中有多個發佈者，每個發佈者的限制都應設定相同，並符合Fastly設定。 原因是在某些情況下，如果從陣列中取出關聯的Dispatcher，則一個發佈者可能會處理比其他發佈者更多的流量。 這表示所有流量都將透過單一剩餘的Dispatcher和發佈程式進行路由，在此情況下，單一發佈程式可能需要所有HTTP連線。

「預設HTTP方法」應從POST設定為GET。 Adobe Commerce GraphQL快取中只會快取GET請求，因此預設方法應一律設為GET。

http連線逾時和http通訊端逾時應該設定為符合Fastly逾時的值。

下圖顯示MagentoCIF GraphQL Client Configuration Factory。 此處顯示的設定僅為範例，需要逐一調整：

![Commerce integration framework組態設定的熒幕擷圖](../assets/commerce-at-scale/cif-config.png)

下圖顯示Fastly後端設定。 此處顯示的設定僅為範例，需要逐一調整：

![Fastly的Commerce管理員組態設定熒幕擷圖](../assets/commerce-at-scale/cif-config-advanced.png)
