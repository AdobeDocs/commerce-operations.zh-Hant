---
title: 更新服務最佳做法
description: 瞭解如何使您的Adobe Commerce在雲基礎架構技術堆棧上保持更新。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 更新服務最佳做法

本文提供建議，讓您的Adobe Commerce保持雲基礎架構技術堆棧的更新，並提供指向有用資源的連結。

## 受影響的產品和版本

Adobe Commerce在雲基礎架構2.4.x及更高版本上

## 更新服務

在Adobe Commerce使用的服務和元件到達或接近生命週期結束之前升級它們。 這有助於跟上PCI合規性並減少安全漏洞。

Starter計畫中的客戶可以在服務升級上自助服務。 請參閱 [更改服務版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 詳細瞭解如何執行此操作。

專業計畫客戶只能在他們的服務升級中自助服務 [整合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html)。 對於生產上的服務升級，您必須 [提交支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 請求升級。

>[!WARNING]
>
>如果沒有48個工作小時的通知，無法將服務升級推送到生產環境。 這是必需的，因為我們需要確保我們有一個基礎架構支援工程師，可以在期望的時間範圍內更新您的配置，同時將生產環境的宕機時間降到最低。

您可以在以下檔案中查看服務版本和終止日期的清單： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml)。

>[!NOTE]
>
>此檔案不能被視為一個真相來源。 如果有疑問，請參閱這些技術的官方供應商網站。

## 其他資訊

[系統要求](../../../installation/system-requirements.md)
