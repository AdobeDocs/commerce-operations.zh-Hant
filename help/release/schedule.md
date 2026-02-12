---
title: 修補程式發行排程
description: 瞭解Adobe計畫何時公佈Adobe Commerce的新修補程式和安全性修正。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 8ee6404271170b19ff27a3ab64711061505494b3
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# 修補程式發行排程

Adobe持續努力在簡化產品升級且可預測之間取得適當的平衡，同時加快改善早期採用者的速度（請參閱[版本設定原則](versioning-policy.md)）。

此排程的目的是提供Adobe計畫針對核心Adobe Commerce PHP應用程式的每個受支援的發行行宣佈[修補程式](versioning-policy.md#patch-release)發行的日期。 修補程式發行可升級核心程式碼基底，確保平台安全、可靠及效能。

>[!NOTE]
>
>若要進一步瞭解新功能、雲端基礎結構和擴充功能發行，請參閱[Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all)發行說明檔案。

除了此頁面上列出的排程品質、安全性及Beta版修補程式之外，Adobe還透過[品質修補程式工具](versioning-policy.md#individual-patch)提供[個別修補程式](../tools/quality-patches-tool/usage.md)的存取權。 此工具可讓您套用、還原及檢視已安裝Adobe Commerce版本可用的所有個別修補程式的一般資訊。

Adobe Commerce修補程式發行版本遵循下列准則：

- **隔離安全性修正** — 個別非累積的[安全性修正](versioning-policy.md#isolated-patch)已視需要發行，並包含所有[支援](lifecycle-policy.md)發行行的安全性修正（包含一般和延伸支援）。

- **安全性修補程式** — 至少每年（5月）都會針對所有[支援的](versioning-policy.md#security-patch-release)發行行發行[安全性修補程式](lifecycle-policy.md)。 這些修補程式包含所有先前發行的獨立安全性修正。 如有必要，Adobe可能會在11月發佈其他安全性修補程式，但並非板上釘釘。

- **修補程式** — 每年（5月）都會發行Adobe Commerce 2.4.x LTS發行系列的完整[修補程式](versioning-policy.md#patch-release) （3年支援期）。

- **Beta修補程式** — 每年發行兩次Adobe Commerce 2.4.x LTS版本系列的[Beta修補程式](versioning-policy.md#beta-patch-release) （三月和十一月）。

如需詳細資訊，請參閱下列影像：

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerce發行行事曆](../assets/release/release-calendar.png)


## 發行通知通道

Adobe會透過下列管道，通知客戶有關新修補程式發行的資訊：

- [Adobe安全性佈告欄和建議](https://helpx.adobe.com/security/security-bulletin.html#magento)
- 電子郵件
- 產品內警示

>[!NOTE]
>
> 如需每個次要、修補程式和安全性版本的發行日期，以及定期支援結束的日期，請參閱[已發行版本](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions)。
