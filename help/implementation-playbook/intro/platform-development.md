---
title: 平台開發原則
description: 使用Adobe Commerce時，了解基本的平台開發原則。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 平台開發原則

在本行動手冊中，我們深入探討Adobe Commerce開發的一些主要標準，包括：

- 功能和技術範圍與開發過程一致
- 與MVC架構一致的開發最佳實務
- 架構注意事項，包括GRA
- 針對指令碼和漏洞攻擊的安全標準
- 擴充功能開發最佳實務
- Web API與REST、SOAP和GraphQL的整合
- 改進編碼和基礎架構的效能
- 測試工具、策略和方法

雖然某些解決方案實施者在實施專案中使用的方法、流程和工具方面可能有自己的偏好，但本行動手冊著重於可在大部分實施中共用的公認最佳實務和方法。

與任何大型IT項目一樣，Adobe Commerce也建立在編碼標準之上，這些標準利用了底層技術(例如PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳做法和標準，以及在Adobe Commerce編碼標準中建立的標準。 遵循這些標準是消除錯誤並改善自訂程式碼品質和可維護性的絕對必要措施。

## Adobe Commerce雲基礎架構

Adobe Commerce on cloud infrastructure是Adobe Commerce軟體的托管、自動化托管平台。 Adobe Commerce雲端基礎架構隨附多種額外功能，讓其與內部部署的Adobe Commerce和Magento Open Source實作不同：

![Adobe Commerce元件資訊圖](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on cloud infrastructure提供了預配置的基礎結構，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]、Elasticsearch技術；以Git為基礎的工作流程，具有自動建置和部署操作，每次在Platform as a Service(PaaS)環境中推送程式碼變更時，都能有效快速開發及持續部署；高度可定製的環境配置檔案和工具；及AWS托管，為線上銷售及零售提供可擴充且安全的環境。

![Adobe Commerce元件資訊圖](../../assets/playbooks/cloud-tech-stack.svg)
