---
title: Adobe商務與Adobe Experience Manager基礎架構協調
description: 調整Adobe商務和Adobe Experience Manager基礎架構，以設定可接受的逾時和連線限制。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# 基礎架構對齊（逾時和連線限制）

有AEM和Adobe商務的設定，以及需要協調的負載平衡器等周邊基礎架構，這些與連線限制和逾時設定相關。

這些限制之間的未對齊將意味著連接最終可能在AEM端被限制，同時Adobe商務能夠處理更多連接。 同樣地，對於逾時設定，未對齊可能表示AEM端發生逾時錯誤，而Adobe商務仍在處理請求。

對於逾時設定，應檢閱並對齊設定，以防止在載入下時出現503逾時錯誤。 要查看的基礎架構和應用程式超時設定包括：

![說明AEM逾時和連線限制的編號圖表](../assets/commerce-at-scale/timeout-settings.svg)

## AEM負載平衡器

假設基礎架構中有一個AWS應用程式負載平衡器以及多個dispatcher/publishers，則應為負載平衡器考慮下列設定：

1. 應審核發佈程式健康狀況檢查，以防止Dispatcher在不必要的早期因載入潮而停止服務。 負載平衡器運行狀況檢查的超時設定應與發佈器超時設定對齊。

   ![螢幕截圖顯示AEM負載平衡器運行狀況檢查](../assets/commerce-at-scale/health-checks.png)

1. 可以停用Dispatcher目標群組黏著度，也可以使用循環負載平衡演算法。 這是假設未使用AEM特定功能或AEM使用者工作階段，而需要設定工作階段黏著度。 此變數假設使用者登入和工作階段管理僅限透過GraphQL進行Adobe商務。

   ![顯示AEM工作階段黏著度屬性的螢幕擷圖](../assets/commerce-at-scale/session-stickiness.png)

1. 請注意，如果您啟用工作階段黏著度，可能會導致系統不快取「Ampley」請求，因為依預設，Amply不會以Set-Cookies標題快取頁面。 Adobe商務會在可快取頁面上設定Cookie(TTL > 0)，但預設的Abmetly VCL會拆解這些Cookie，讓Abmetly快取運作。 如果頁面未快取，請檢查您可能使用的任何自訂Cookie，並上傳Appeyt VCL並重新檢查網站。

## Dispatcher逾時設定

Dispatcher「轉譯」選項中的/timeout會指定存取AEM發佈例項的連線逾時（以毫秒為單位）。 如果存在單獨的負載平衡器來處理超時設定，則應審查此設定，並使用預設設定「0」（無限超時）。

如果基礎架構中沒有負載平衡器，則應在Dispatcher /timeout設定中指定逾時設定，其值應與發佈程式中的GraphQL逾時設定相符。

## 發佈者

發佈商GraphQL連接限制和超時：起初，Adobe商務CIF GraphQL用戶端設定工廠OSGI中的「最大HTTP連線數」設定應設為預設的「快速最大連線數」限制，目前此限制設為200。 即使AEM伺服器陣列中有多個發佈者，每個發佈者的限制也應設定相同，與「Ampley」設定相符。 原因在於，在某些情況下，如果將相關聯的Dispatcher從伺服器陣列中取出，則某個發佈者處理的流量可能會比其他發佈者多。 這表示所有流量都會經由單一剩餘的Dispatcher和發佈者路由，在這種情況下，單一發佈者可能需要所有HTTP連線。

「預設HTTP方法」應從POST設定為GET。 只有GET請求會在Adobe商務GraphQL快取中進行快取，因此應一律將預設方法設為GET。

http連接超時和http套接字超時應設定為與Ampeitt超時相匹配的值。

下圖顯示MagentoCIF GraphQL客戶端配置工廠。 此處顯示的設定僅為範例，需逐一調整：

![Commerce整合架構組態設定的螢幕擷圖](../assets/commerce-at-scale/cif-config.png)

下圖顯示「Ompey」後端設定。 此處顯示的設定僅為範例，需逐一調整：

![Appliet的Commerce Admin配置設定螢幕截圖](../assets/commerce-at-scale/cif-config-advanced.png)
