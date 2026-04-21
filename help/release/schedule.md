---
title: 修補程式發行排程
description: 了解 Adobe 規劃於何時公佈發行 Adobe Commerce 的新修補程式和安全性修正。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# 修補程式發行排程

Adobe持續努力在簡化產品升級且可預測之間取得適當的平衡，同時加快改善早期採用者的速度（請參閱[版本設定原則](versioning-policy.md)）。

此排程的目的是提供Adobe計畫針對核心Adobe Commerce PHP應用程式的每個受支援的發行行宣佈[修補程式](versioning-policy.md#patch-release)發行的日期。 修補程式發行可升級核心程式碼基底，確保平台安全、可靠及效能。

>[!NOTE]
>
>若要進一步瞭解新功能、雲端基礎結構和擴充功能發行，請參閱[Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all)發行說明檔案。

除了此頁面上列出的排程品質、安全性及Beta版修補程式之外，Adobe還透過[品質修補程式工具](versioning-policy.md#individual-patch)提供[個別修補程式](../tools/quality-patches-tool/usage.md)的存取權。 此工具可讓您套用、還原及檢視已安裝Adobe Commerce版本可用的所有個別修補程式的一般資訊。

Adobe Commerce修補程式發行版本遵循下列准則：

- **隔離的安全性修補程式檔案** — 個別非累積的[安全性修補程式檔案](versioning-policy.md#isolated-security-patch-file)可獨立發行，以啟用更快速的修正，並整合到下一個完整的安全性修補程式中。 若要套用隔離的安全性修補程式檔案，客戶必須在其支援的發行版本行上使用最新的僅限安全性的修補程式發行版本（最新的 — p版本），因為隔離的安全性修補程式是專門針對該版本進行測試的。

- **安全性修補程式** — 至少每年會針對所有[支援的](versioning-policy.md#security-patch-release)發行行發行[安全性修補程式](lifecycle-policy.md)。 這些修補程式包含所有先前發行的安全性、法規遵循和品質Hotfix。  如有必要，Adobe可能會發行其他安全性修補程式，但不保證一定會發行。

- **修補程式** — 每年（5月）都會發行Adobe Commerce 2.4.x LTS發行系列的完整[修補程式](versioning-policy.md#patch-release) （3年支援期）。

- **Alpha修補程式** — 每年都會發行適用於Adobe Commerce 2.4.x LTS發行行的[Alpha修補程式](versioning-policy.md#alpha-patch-release)。

- **Beta修補程式** — 每年都會發行適用於Adobe Commerce 2.4.x LTS發行系列的[Beta修補程式](versioning-policy.md#beta-patch-release)。

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
