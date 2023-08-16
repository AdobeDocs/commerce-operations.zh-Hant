---
title: 平台開發原則
description: 瞭解使用Adobe Commerce時的基本平台開發原則。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 平台開發原則

在本教戰手冊中，我們深入探討Adobe Commerce開發的一些主要標準，包括：

- 符合開發流程的功能和技術範圍
- 符合MVC架構的開發最佳實務
- 架構考量，包括GRA
- 針對指令碼和漏洞的安全標準
- 擴充功能開發最佳實務
- Web API與REST、SOAP和GraphQL整合
- 針對編碼和基礎建設的效能改良
- 測試工具、策略和方法

雖然某些解決方案實作者在實施專案中使用的方法、流程和工具時，可能有各自的偏好，但本Playbook的重點在於可在大多數實作中分享的公認最佳實務和方法。

像任何大型IT專案一樣，Adobe Commerce建置在編碼標準上，這些標準運用基礎技術(例如PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳實務和標準化，以及Adobe Commerce編碼標準中建立的標準。 絕對必須遵循這些標準，才能消除錯誤，並改善自訂程式碼的品質和可維護性。

## 雲端基礎結構上的Adobe Commerce

雲端基礎結構上的Adobe Commerce是適用於Adobe Commerce軟體的受管理、自動化託管平台。 雲端基礎結構上的Adobe Commerce提供多種其他功能，使其有別於內部部署Adobe Commerce和Magento Open Source實施：

![Adobe Commerce元件資訊圖形](../../assets/playbooks/commerce-cloud.svg)

雲端基礎結構上的Adobe Commerce提供預先布建的基礎結構，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]和Elasticsearch技術；Git型工作流程，具有自動建置和部署作業，可在每次在Platform as a Service (PaaS)環境中推送程式碼變更時，有效率地快速開發和持續部署；可高度自訂的環境設定檔案和工具；以及AWS託管，可為線上銷售和零售提供可擴充且安全的環境。

![Adobe Commerce元件資訊圖形](../../assets/playbooks/cloud-tech-stack.svg)
