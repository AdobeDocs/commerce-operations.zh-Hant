---
title: 更新服務最佳實務
description: 了解如何讓Adobe Commerce在雲端基礎架構技術堆疊上持續更新。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# 更新服務最佳實務

本文提供相關建議，讓您的Adobe Commerce在雲端基礎架構技術堆疊中保持更新，並提供實用資源的連結。

## 受影響的產品和版本

Adobe Commerce on cloud infrastructure 2.4.x及更新版本

## 更新服務

升級Adobe Commerce使用的服務和元件，再等到或接近服務終止日期。 這有助於跟上PCI合規性，並減少安全漏洞。

入門計畫的客戶可以自助升級服務。 請參閱 [更改服務版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 以取得如何執行此動作的詳細資訊。

專業計畫的客戶只能在其 [整合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 若是生產上的服務升級，您必須 [提交支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 請求升級。

>[!WARNING]
>
>若未通知我們的基礎架構團隊48個工作小時，無法將服務升級推送到生產環境。 這是必需的，因為我們需要確保有基礎架構支援工程師可以在所需的時間範圍內更新您的配置，而生產環境的停機時間最少。

您可以在下列檔案中檢視服務版本和終止日期清單： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>此檔案不能視為單一真相來源。 如果有疑問，請參閱這些技術的官方供應商網站。

## 其他資訊

[系統需求](../../../installation/system-requirements.md)
