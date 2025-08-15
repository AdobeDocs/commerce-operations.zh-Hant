---
title: Adobe Commerce 2.4.2安全性修補程式發行說明
description: 瞭解Adobe Commerce 2.4.2版的安全性修補程式發行版本中包含的安全性錯誤修正、安全性增強功能和其他安全性相關更新。
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Adobe Commerce 2.4.2安全性修補程式的發行說明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

Adobe Commerce 2.4.2-p2安全性版本針對2.4.2先前版本中發現的弱點提供安全性錯誤修正。

如需安全性錯誤修正的最新資訊，請參閱[Adobe安全性公告APSB21-64](https://helpx.adobe.com/tw/security/products/magento/apsb21-64.html)。

## 套用`AC-3022.patch`以繼續提供DHL作為運送承運商

DHL已匯入schema 6.2版，並將在不久的未來淘汰schema 6.0版。 支援DHL整合的Adobe Commerce 2.4.4及舊版僅支援6.0版。部署這些版本的商戶應儘早套用`AC-3022.patch`，以繼續提供DHL作為運送承運商。 請參閱[套用修補程式，以繼續提供DHL作為運送業者](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知識庫文章，以取得有關下載和安裝修補程式的資訊。
