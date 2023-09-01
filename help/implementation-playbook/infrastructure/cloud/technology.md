---
title: 雲端基礎結構技術
description: 進一步瞭解Adobe在雲端基礎結構上Adobe Commerce所使用的技術集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# 技術

雲端基礎結構上的Adobe Commerce使用數個軟體解決方案來支援該平台。 請參閱 _雲端指南_ 如需更多詳細資料：

- [專業環境架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [入門環境架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## 功能和優點

- 虛擬私人雲端(VPC)中的三個專用執行個體，在三個獨立的可用區域或資料中心間具有彈性負載平衡器。
- 針對可能導致單一執行個體失敗的事件，提供更高的恢復能力。 例如，整個AWS可用區域或資料中心發生中斷。
- 可在整個棧疊中進行零停機時間縮放，包括網頁、快取、搜尋和資料庫。
