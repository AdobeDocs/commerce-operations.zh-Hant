---
title: Adobe Commerce的管理警報：磁碟警告警報
description: 本文提供當您在 [!DNL New Relic]中收到Adobe Commerce的警告磁碟警示時的疑難排解步驟。 需要立即採取行動來解決問題。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3ad22e3a113b52da6d6095103376fee6e36dc804
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Adobe Commerce的管理警報：磁碟警告警報

本文提供當您在[!DNL New Relic]中收到Adobe Commerce的警告磁碟警示時的疑難排解步驟。 需要立即採取行動來解決問題。 根據您選取的警報通知通道，警報看起來類似以下內容。

![磁碟警告警示](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，Pro規劃架構。

## 問題

如果您已為Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)註冊了個受管理的警示，且超過一或多個警示臨界值，則您將在[!DNL New Relic]中收到警示。 這些警報由Adobe開發，可讓客戶運用支援和工程部門的見解獲得標準集合。

<u> **做！** </u>

* 中止任何排定的部署，直到清除此警示為止。
* 如果您的網站沒有回應或完全沒有回應，請立即將網站置於維護模式。 如需相關步驟，請參閱《Commerce安裝指南》中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 請務必將您的IP新增至劐免IP位址清單，以確保您仍可存取您的網站以進行疑難排解。 如需相關步驟，請參閱《Commerce安裝指南》中的[維護IP位址劐免清單](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)。

<u> **不要！** </u>

* 啟動其他行銷活動，可能會為您的網站帶來其他頁面檢視。
* 執行索引器或其他cron，可能會在CPU或磁碟上造成額外的壓力。
* 執行任何主要管理工作(例如Commerce管理、資料匯入/匯出)。
* 清除您的快取。 如果您在調查並解決警示原因之前，執行了任何「不執行」動作，您的網站可能會停止回應（如果您尚未發生網站中斷）。

## 解決方案

請依照下列步驟，找出原因並加以疑難排解：

1. 在[!DNL New Relic]中，檢閱磁碟以取得最高使用率。 如需相關步驟，請參閱[[!DNL New Relic] 基礎結構監視主機頁面上的&#x200B;**[!UICONTROL Storage]**&#x200B;標籤： [!UICONTROL Storage]標籤](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage)：
   * 如果您在[!DNL New Relic]中看到磁碟使用量緩慢增加，請嘗試下列選項：
      * 調整空間配置，最佳化磁碟空間。 如需相關步驟，請參閱雲端上的Commerce指南中的[管理磁碟空間](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space)。 您可能還需要請求更多磁碟空間(請聯絡您的Adobe帳戶團隊)。
      * 清除MySQL的磁碟空間。 如需步驟，請參閱[MySQL磁碟空間不足](http://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud)。
      * 如果[!DNL New Relic]顯示磁碟使用量快速增加，這可能表示發生問題，導致目錄中的檔案快速增加。 進行下列檢查：
         1. 在CLI/終端機中執行以下命令，檢查整體磁碟空間以找出問題： `df -h`
         1. 在識別具有意外大且磁碟使用量增加的目錄後，您需要檢查受影響的檔案系統。 下列範例顯示如何檢查檔案目錄`pub/media/`。 這是Adobe Commerce用來儲存記錄檔和大型媒體檔案的目錄。 不過，您應該針對顯示非預期磁碟使用量的任何目錄執行此命令： `du -sch ~/pub/media/*`。

如果終端機的輸出顯示其中某個目錄中的檔案在磁碟使用量中迅速增加，並且您知道不需要檔案的內容，請考慮移除檔案。 如果您不喜歡執行此動作，請[提交Adobe Commerce支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)。
