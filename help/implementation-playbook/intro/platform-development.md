---
title: 平台開發原則
description: 使用Adobe商務時，請了解基本的平台開發原則。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# 平台開發原則

在本行動手冊中，我們深入探討Adobe商務開發的一些主要標準，包括：

- 功能和技術範圍與開發過程一致
- 與MVC架構一致的開發最佳實務
- 架構注意事項，包括GRA
- 針對指令碼和漏洞攻擊的安全標準
- 擴充功能開發最佳實務
- Web API與REST、SOAP和GraphQL的整合
- 改進編碼和基礎架構的效能
- 測試工具、策略和方法

雖然某些解決方案實施者在實施專案中使用的方法、流程和工具方面可能有其自己的偏好，但本行動手冊著重於可在大部分實施中共用的公認最佳實務和方法。

與任何大型IT項目一樣，Adobe商務也建立在編碼標準之上，這些標準利用了底層技術（例如PHP/Zend、Symfony、JavaScript、jQuery和HTML）的最佳做法和標準，以及在Adobe商務編碼標準中建立的標準。 遵循這些標準是消除錯誤並改善自訂程式碼品質和可維護性的絕對必要措施。

## Adobe雲基礎架構上的商務

Adobe雲端基礎架構上的Adobe商務是適用於雲端商務軟體的受管式自動化托管平台。 雲基礎架構上的Adobe商務隨附多種額外功能，與內部Adobe商務和Magento Open Source實作不同：

![Adobe商務元件資訊](../../assets/playbooks/commerce-cloud.svg)

Adobe雲基礎架構上的Commerce提供了預配置的基礎架構，包括PHP、MySQL、Redis、RabbitMQ和Elasticsearch技術；以Git為基礎的工作流程，具有自動建置和部署操作，每次在Platform as a Service(PaaS)環境中推送程式碼變更時，都能有效快速開發及持續部署；高度可定製的環境配置檔案和工具；以及AWS托管，為線上銷售和零售提供可擴展且安全的環境。

![Adobe商務元件資訊](../../assets/playbooks/cloud-tech-stack.svg)
