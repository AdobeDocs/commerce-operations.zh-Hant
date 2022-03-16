---
title: 雲基礎架構環境
description: 為正確的使用情形使用適當的環境。
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 環境

Adobe Commerce雲基礎架構專業架構支援您可以用來開發、test和啟動儲存的環境。 每個環境都包含資料庫和Web伺服器。 Adobe Commerce利用的四個環境是：

- **整合** — 提供單個環境分支，您最多可以建立四個附加的環境分支。 這允許最多將五個活動分支部署到平台即服務(PaaS)容器。

- **暫存** — 提供部署到專用「基礎架構即服務」(IaaS)容器的單個環境分支。

- **生產** — 提供部署到專用「基礎架構即服務」(IaaS)容器的單個環境分支。

- **全局主節點** — 提供部署到平台即服務(PaaS)容器的主分支。

![顯示Adobe Commerce雲環境之間關係的圖](../../../assets/playbooks/environment-diagram.svg)

## Git分支

整合環境提供了單個基本整合分支，其中包含部署到平台即服務(PaaS)容器的Adobe Commerce代碼。

Adobe Commerce雲基礎架構環境支援靈活、連續的整合流程。 首先將整合分支克隆到本地項目資料夾。 建立新分支或多個分支以開發新功能、配置更改和添加擴展。 通過開發的代碼分支和相應的配置檔案，您的代碼更改可以合併到整合分支中，以便進行更全面的測試。

![示出Adobe Commerce雲環境基於Git的分支策略的圖](../../../assets/playbooks/branching-diagram.svg)
