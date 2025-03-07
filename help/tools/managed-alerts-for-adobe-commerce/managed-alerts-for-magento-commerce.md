---
title: Adobe Commerce的管理警報
description: 如果您是雲端基礎結構專業版的Adobe Commerce規劃架構客戶，則可以使用受管理警報來瞭解您網站的健康情況。 如果您是雲端基礎結構入門計畫架構客戶的Adobe Commerce，您將只會收到 [!DNL Apdex] 和錯誤率條件的警示。
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: efb58b920a9b72ac96bbd28aaae6210ede84e24f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Adobe Commerce的管理警報


我們設定了重要的儀表板和警示，協助您瞭解網站何時達到關鍵儲存空間和[!DNL Apdex]等級（使用者對應用程式和服務回應時間的滿意度）。 這可協助您在注意到回應時間緩慢或中斷之前採取行動。 您將能夠使用下列文章來疑難排解警示。 在使用警示之前，請先設定通知通道。 請參閱雲端上的Commerce指南中的[[!DNL New Relic] 設定通知通道](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service)。

>[!NOTE]
>
>如果Adobe Commerce警示原則的已管理警示無法使用，可能是因為此帳戶是新建的或最近已設定[!DNL New Relic]。 每個星期二都會執行一個程式，將警示原則新增至這些帳戶。 下次程式執行後的第二天，您應該可以使用警示原則。 如果原則仍然遺失，[請提交Adobe Commerce支援請求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)並包含您的專案ID。

請參閱下表中的知識庫文章連結，提供這些警示的疑難排解步驟：

* Adobe Commerce的管理警報： CPU警告警報
* Adobe Commerce的管理警報：CPU嚴重警報
* Adobe Commerce的管理警報：記憶體警告警報
* Adobe Commerce的管理警示：記憶體嚴重警示
* 已管理Adobe Commerce的警示： [!DNL Apdex]警告警示
* 已管理Adobe Commerce的警示： [!DNL Apdex]嚴重警示
* Adobe Commerce的管理警報：磁碟警告警報
* Adobe Commerce的管理警示：磁碟嚴重警示
* 在Adobe Commerce上管理警報：MariaDB警報
* Adobe Commerce上的受管理警報： [!DNL Redis]記憶體警告警報
* Adobe Commerce上的受管理警示： [!DNL Redis]記憶體嚴重警示

>[!NOTE]
>
>「警告警示」和「嚴重警示」的設定臨界值是根據我們正在使用客戶群的歷史效能資料進行的研究而定，並代表Adobe Commerce支援和工程團隊的最新深入分析。 請注意，這些臨界值可能會根據最新的持續分析而有所變更。 一般的警報流程是接收警報，其嚴重性會由低到高的順序排列。 因此，在收到「嚴重」警示之前，您可能會收到「警告」警示。 請參閱文章連結以了解疑難排解步驟。

| 嚴重程度 | CPU | 記憶體 | 磁碟 | [!DNL Apdex] | MariaDB | [!DNL Redis]記憶體 | 疑難排解文章 |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| 警告 | ✅ |        |      |       |         |              | [Adobe Commerce的管理警示： CPU警告警示](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| 關鍵 | ✅ |        |      |       |         |              | [Adobe Commerce的管理警示： CPU嚴重警示](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| 警告 |     | ✅ |      |       |         |              | [Adobe Commerce的管理警示：記憶體警告警示](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| 關鍵 |     | ✅ |      |       |         |              | [Adobe Commerce的Managed警示：記憶體嚴重警示](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| 警告 |     |        |      | ✅ |         |              | [Adobe Commerce的Managed警示： [!DNL Apdex] 警告警示](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| 關鍵 |     |        |      | ✅ |         |              | [Adobe Commerce受管理的警示： [!DNL Apdex] 嚴重警示](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| 警告 |     |        | ✅ |       |         |              | [Adobe Commerce的管理警示：磁碟警告警示](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| 關鍵 |     |        | ✅ |       |         |              | [Adobe Commerce的Managed警示：磁碟嚴重警示](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| 警告與嚴重 |     |        |      |       | ✅ |              | 在Adobe Commerce上[受管理的警示： MariaDB警示](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| 警告 |     |        |      |       |         | ✅ | [Adobe Commerce上的Managed警示： [!DNL Redis] 記憶體警告警示](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| 關鍵 |     |        |      |       |         | ✅ | [Adobe Commerce上的Managed警示： [!DNL Redis] 記憶體嚴重警示](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
