---
title: 平台開發原則
description: 瞭解與Adobe Commerce合作時的基本平台開發原則。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 平台開發原則

在本手冊中，我們深入探討Adobe Commerce發展的一些主要標準，包括：

- 根據開發過程進行功能和技術範圍界定
- 開發與MVC體系結構相協調的最佳做法
- 體系結構考慮事項，包括GRA
- 針對指令碼和漏洞的安全標準
- 擴展開發最佳做法
- Web API與REST、SOAP和GraphQL的整合
- 編碼和基礎架構的效能改進
- 測試工具、策略和方法

雖然某些解決方案實施者在涉及整個實施項目中使用的方法體系、流程和工具時可能有自己的偏好，但本手冊側重於可在大多數實施中共用的公認最佳做法和方法體系。

與任何大型IT項目一樣，Adobe Commerce建立在編碼標準之上，這些標準利用了底層技術(例如PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳做法和標準化，以及在Adobe Commerce編碼標準中建立的標準。 遵循這些標準是消除錯誤和提高定制代碼的質量和可維護性的絕對必要。

## Adobe Commerce在雲基礎架構上

Adobe Commerce雲基礎架構是Adobe Commerce軟體的托管、自動托管平台。 Adobe Commerce在雲基礎架構上提供了多種附加功能，使其有別於內部Adobe Commerce和Magento Open Source實施：

![Adobe Commerce元件資訊圖形](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce雲基礎架構提供預配置的基礎架構，包括PHP、MySQL、Redis、RabbitMQ和Elasticsearch技術；一種基於Git的工作流，具有自動構建和部署操作，以便每次在平台即服務(PaaS)環境中推送代碼更改時，都能高效快速開發和持續部署；高度可定製的環境配置檔案和工具；以及AWS的主機托管，為線上銷售和零售提供可擴展且安全的環境。

![Adobe Commerce元件資訊圖形](../../assets/playbooks/cloud-tech-stack.svg)
