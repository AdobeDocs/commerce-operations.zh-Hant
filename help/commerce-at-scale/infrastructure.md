---
title: Adobe Commerce和Adobe Experience Manager基礎架構協調
description: 調整您的Adobe Commerce和Adobe Experience Manager基礎架構以設定可接受的超時和連接限制。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# 基礎架構調整（超時和連接限制）

有與Adobe Commerce和AEM周圍的基礎架構（如負載平衡器）的設定需要協調，這些設定與連接限制和超時設定相關。

這些限制之間的不協調意味著，連接最終可能會被AEM側限制，而Adobe Commerce能夠處理更多連接。 同樣，對於超時設定，未對準可能意味著在Adobe Commerce仍在處AEM理請求的同時出現超時錯誤。

對於超時設定，應檢查並對齊設定，以防止在載入時出現503個超時錯誤。 要查看的基礎架構和應用程式超時設定有幾個：

![描述超時和連接限制的編號圖AEM](../assets/commerce-at-scale/timeout-settings.svg)

## 負載平衡AEM器

假定基礎架構中有一個AWS應用程式負載平衡器和多個調度程式/發佈程式 — 應考慮負載平衡器的以下設定：

1. 應檢查發佈器運行狀況檢查，以防止調度程式因負載劇增而過早退出服務。 負載平衡器運行狀況檢查的超時設定應與發佈器超時設定對齊。

   ![顯示負載平衡AEM器運行狀況檢查的螢幕快照](../assets/commerce-at-scale/health-checks.png)

1. 可以禁用Dispatcher目標組粘性，並可以使用Round Robin負載平衡算法。 這假設沒有使用AEM需要設AEM置會話粘性的特定功能或用戶會話。 它假定用戶登錄和會話管理僅通過GraphQL在Adobe Commerce。

   ![螢幕截圖顯示AEM會話粘性屬性](../assets/commerce-at-scale/session-stickiness.png)

1. 請注意，如果確實啟用了會話粘性，這可能會導致Abmistey請求不被快取，因為預設情況下，Abmisty不會使用Set-Cookie標頭快取頁面。 Adobe Commerce甚至在可快取頁面(TTL > 0)上也會設定cookie，但預設的Reblish VCL會在可快取頁面上刪除這些cookie，以便Reblish快取工作。 如果頁面沒有快取，請檢查您可能正在使用的任何自定義Cookie，並上載Abmeist VCL並重新檢查站點。

## 調度程式超時設定

調度程式「呈現」選項中的/timeout指定訪問發佈實例的連接超AEM時（以毫秒為單位）。 如果存在單獨的負載平衡器來處理超時設定，則應檢查此設定，並使用預設設定「0」（無限超時）。

如果基礎架構中沒有負載平衡器，則應在調度程式/timeout設定中指定超時設定，其值應與發佈伺服器中的GraphQL超時設定匹配。

## 出版商

發佈伺服器GraphQL連接限制和超時：最初，Adobe CommerceCIF GraphQL客戶端配置工廠OSGI中的最大HTTP連接數應設定為預設的「Abmishemy maximum connections」限制，該限制當前設定為200。 即使場中有多個發佈AEM器，也應在每個發佈器中設定相同的限制，與「Rebist」設定相匹配。 原因是，在某些情況下，如果將關聯的調度程式從伺服器場中取出，則一個發佈伺服器處理的通信量可能比其他發佈伺服器要多。 這意味著所有通信都將通過剩餘的單個調度程式和發佈程式進行路由，在這種情況下，單個發佈程式可能需要所有HTTP連接。

「預設HTTP方法」應從POST設定為GET。 只有GET請求在Adobe CommerceGraphQL快取中快取，因此預設方法應始終設定為GET。

http連接超時和http套接字超時應設定為與Abmistifet匹配的值。

下圖顯示了MagentoCIF GraphQL客戶端配置工廠。 此處顯示的設定僅是示例，需要逐個案例進行調整：

![Commerce整合框架配置設定的螢幕快照](../assets/commerce-at-scale/cif-config.png)

以下影像顯示了Affiest後端配置。 此處顯示的設定僅是示例，需要逐個案例進行調整：

![Apphist的Commerce Admin配置設定螢幕快照](../assets/commerce-at-scale/cif-config-advanced.png)
