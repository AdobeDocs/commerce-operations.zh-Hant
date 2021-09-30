---
title: 雲基礎架構環境
description: 針對正確的使用案例使用正確的環境。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 環境

Adobe雲端基礎架構上的商務Pro架構支援環境，您可以用來開發、測試和啟動您的商店。 每個環境都包含資料庫和Web伺服器。 Adobe商務採用的四個環境為：

- **整合** — 提供單一環境分支，您最多可以建立四個其他環境分支。這最多允許部署到「平台即服務」(PaaS)容器的五個活動分支。

- **測試** — 提供部署到專用基礎架構即服務(IaaS)容器的單個環境分支。

- **生產** — 提供部署到專用基礎架構即服務(IaaS)容器的單一環境分支。

- **全局主** — 提供部署到Platform-as-a-Service(PaaS)容器的主分支。

![顯示AdobeCommerce雲環境之間關係的圖表](../../../assets/playbooks/environment-diagram.svg)

## Git分支

整合環境提供單一基礎整合分支，內含部署至Platform-as-a-Service(PaaS)容器的Adobe商務程式碼。

雲基礎架構環境上的Adobe商務支援靈活、持續的整合流程。 首先，將整合分支複製到本機專案資料夾。 建立新分支或多個分支，以開發新功能、設定變更和新增擴充功能。 透過開發的程式碼分支和對應的設定檔案，您的程式碼變更已準備好合併至整合分支，以進行更全面的測試。

![圖表顯示Commerce雲環境的Git型分支策略Adobe](../../../assets/playbooks/branching-diagram.svg)
