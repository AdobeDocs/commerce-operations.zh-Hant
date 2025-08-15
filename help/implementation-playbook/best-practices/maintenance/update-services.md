---
title: 更新服務最佳實務
description: 瞭解如何讓您的Adobe Commerce在雲端基礎結構技術棧疊上保持更新。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 更新服務最佳實務

本文提供建議讓雲端基礎結構技術棧疊上的Adobe Commerce保持更新，並提供實用資源的連結。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.x和更新版本

## 更新服務

在Adobe Commerce使用的服務和元件達到或接近生命週期結束日期之前升級。 這有助於遵循PCI法規並減少安全性漏洞。

入門計畫客戶可自助服務升級。 請參閱[變更服務版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version)，以取得如何執行此動作的詳細資訊。

Pro方案客戶只能在其[整合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html)中自助服務升級。 若要在生產環境中升級服務，您必須[提交支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)以要求升級。

>[!WARNING]
>
>若未提前48個營業時間通知Adobe的基礎建設團隊，服務升級就無法推送至生產環境。 這是必要的，因此Adobe可以確保基礎建設支援工程師在所需時間範圍內更新您的設定，並將生產環境的停機時間降到最低。 Adobe建議您在服務升級期間將網站置於維護模式。

您可以在下列檔案中檢視服務版本清單和生命週期結束日期： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml)。

>[!NOTE]
>
>此檔案不能視為單一信任來源。 如有疑問，請參閱官方廠商網站以瞭解這些技術。

## 其他資訊

[系統需求](../../../installation/system-requirements.md)
