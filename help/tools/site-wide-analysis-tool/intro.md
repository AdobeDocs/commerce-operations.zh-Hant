---
title: '[!DNL Site-Wide Analysis Tool]'
description: 瞭解 [!DNL Site-Wide Analysis] 工具、其用途、安裝過程以及如何取得存取權
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 99e5cf727d88de3e03c8076bbd11114e758c19ab
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce內部部署客戶將停止使用[!DNL Site-Wide Analysis Tool]。

本指南提供[!DNL Site-Wide Analysis Tool]的整體概觀。 它描述了使用的逐步安裝說明，以及如何存取工具。

## 什麼是[!DNL Site-Wide Analysis Tool]？

[!DNL Site-Wide Analysis Tool]是主動式自助服務工具和中央存放庫，其中包含詳細的系統分析和建議，以確保Adobe Commerce安裝的安全性和可操作性。 它提供全天候的即時效能監控、報告和建議，以找出潛在問題，並更清楚地瞭解網站健康狀況、安全性和應用程式設定。 這有助於縮短解決時間，並改善網站穩定性與效能。

>[!NOTE]
>
>[!DNL Site-Wide Analysis Tool]報告系統層級資料。 如需Adobe Commerce產品、銷售、行銷和其他商務應用程式資料的相關報表，請參閱[Adobe Commerce報表](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/reports-menu)。

![全網站分析工具儀表板](../../assets/tools/swat-dashboard.png){zoomable="yes"}

請參閱此[簡介影片](https://www.youtube.com/watch?v=KW2R8ki_RG4)以瞭解更多資訊。

## 工具概述

- **儀表板**
   - 顯示系統整體健康狀況，包含偵測到的問題通知以及依優先順序的特定建議。<br>
此外也包含歷史圖表，以追蹤網站健康情況在一段時間內的變化。
   - 顯示可讓您存取的&#x200B;**[!UICONTROL Security Center Widget]**：
      - [技術 [!DNL Stack] 版本相容性 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=zh-Hant)
      - [Adobe安全性公告](https://helpx.adobe.com/tw/security/security-bulletin.html)
      - 來自[&#x200B; [!DNL Security Scan Tool]的](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hant)建議
      - [[!DNL Site-Wide Analysis Tool] 最佳實務安全性建議](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=zh-Hant)

- **資訊** — 提供客戶連絡資訊和目前票證的摘要，以及每個Adobe Commerce產品的詳細資訊。

- **建議** — 根據最佳做法列出建議，以解決在您的網站上偵測到的問題：
   - 若變更需要更新基礎結構，請提交支援請求。
   - 若變更需要更新應用程式，請自行進行變更。
   - 如需需要手動介入的變更，例如[程式碼部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=zh-Hant#deployment-workflow)，請向您的系統管理員或開發人員尋求協助。

- **例外狀況** — 列出應用程式因無錯誤處理常式的異常狀況所擲回的錯誤。

- **擴充功能** — 列出所有協力廠商擴充功能和協力廠商程式庫。

- **修補程式** — 與[!DNL Quality Patches Tool]整合，提供您Adobe Commerce執行個體專屬的所有可用修補程式清單。

## 整合其他Adobe Commerce支援工具

在一個位置檢視有關您網站的所有重要深入分析。 [!DNL Site-Wide Analysis Tool]可讓您直接存取[!UICONTROL Security Center Widget]、[!DNL Upgrade Compatability Tool]和[!DNL Managed Alerts]的資訊。

- [**[!UICONTROL Security Center Widget]**] — 顯示您網站的安全性深入分析。<br>
顯示的安全性資訊包含[技術 [!DNL Stack] 版本相容性與 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=zh-Hant), [Adobe Security Bulletin](https://helpx.adobe.com/tw/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hant), and [[!DNL Site-Wide Analysis Tool] 最佳實務安全性建議](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=zh-Hant)。<br>
[[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hant)會主動偵測惡意軟體，並在其存放區遭到破壞時通知客戶，藉此為Adobe Commerce和Magento Open-Source客戶提供其存放區安全性狀態的即時深入分析。

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) — 針對目標升級版本執行Adobe Commerce的自訂執行個體，並傳回必須解決的嚴重問題、錯誤和警告摘要，讓升級分析程式更容易、更快、更便宜。

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) — 監控多個量度以主動追蹤平台的效能，並提供疑難排解問題的特定指示，讓商家可以避免重大停機時間，並隨時瞭解其CPU、應用程式效能、磁碟、記憶體和資料庫。

## 本指南適用對象？

想要更深入瞭解其Adobe Commerce網站的商家和合作夥伴。 它可讓商戶改善其客戶體驗，並在最佳實務建議和基本問題上更緊密地保持一致。

## [!DNL Site-Wide Analysis Tool]展示

觀看此影片以瞭解[!DNL Site-Wide Analysis Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
