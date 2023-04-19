---
title: "[!DNL Dashboard]"
description: 了解 [!DNL Dashboard] 標籤 [!DNL Site-Wide Analysis Tool]、元素、使用時機、優點和最佳實務。
source-git-commit: 78cc20b7a65bff641f6849f6c2566cf5ad2afbd1
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

此 [!UICONTROL Dashboard] 頁面顯示一覽 [!DNL widgets] 提供Adobe Commerce網站健康狀況和目前狀態的「單一玻璃檢視窗格」。 每個 [!DNL widget] 包含每個功能頁面、每個工具本身或報表的存取連結(視 [!DNL widget])。
還有 [!UICONTROL External Resources] Adobe Commerce的連結，包括 [Adobe Commerce幫助中心支援知識庫（幫助中心）](https://support.magento.com/), [Adobe Commerce開發人員檔案(DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [安全中心](https://magento.com/security)，和 [Adobe Commerce觀察](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## 元素

* **[!UICONTROL Recommendations]**:顯示您網站的最佳實務建議。 Recommendations（發現的問題和要修正的建議）會依優先順序排序 — P0（嚴重）到P4（通知）。
Recommendations包含說明、建議、網站影響、根本原因、案例/先決條件，以及使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**:透過分析其中安裝的所有模組和核心程式碼，根據特定版本檢查Adobe Commerce自訂例項。 它會傳回重要問題、錯誤和警告的清單，在升級至最新版Adobe Commerce之前必須解決這些問題。 它也會找出程式碼中必須修正的潛在問題，才能嘗試升級至更新版的Adobe Commerce。
此 [!UICONTROL Upgrade Compatibility Tool] 可讓您識別何時對自訂功能進行了核心程式碼變更。

* **[!UICONTROL Security Center Widget]**:顯示您網站的安全性分析。
顯示的安全資訊包括 [技術 [!DNL Stack] 版本合規性，與 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 最佳實務安全性Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
此 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) 監控Adobe Commerce網站的安全風險。 它可以主動和高效地檢測商家商店上的惡意軟體，並在存在任何安全風險、惡意軟體或威脅時通知商家，並可以識別缺少的Adobe Commerce修補程式和更新。

* **[!UICONTROL Extensions]**:顯示目前安裝在您的Adobe Commerce執行個體上的擴充功能。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 此處列出的擴充功能會提供可用的資訊。

* **[!UICONTROL Alerts]**:顯示最新 [!DNL New Relic Managed Alerts] 例如Adobe Commerce例項。 深入了解 [Adobe Commerce的受管警報](https://support.magento.com/hc/en-us/articles/360045806832) 以及如何 [存取New Relic服務](https://support.magento.com/hc/en-us/articles/360039127712) 在Adobe Commerce支援知識庫中。

* **[!UICONTROL Non-recommended software in use]**:根據您的Adobe Commerce版本，顯示您的Adobe Commerce執行個體目前使用的非建議軟體。 不推薦的軟體由 [!UICONTROL Name], [!UICONTROL Installed Version]，和 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**:根據您可能已安裝的修補程式和您的Adobe Commerce版本，顯示任何建議修補程式的簡短清單。 建議修補程式的完整清單位於 **[!UICONTROL Patches]** 功能標籤中 [!DNL Site-Wide Analysis Tool]. 修補程式由 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 列出的所有修補程式都與您當前的Adobe Commerce實例相容。
如果沒有建議為您的Adobe Commerce執行個體顯示修補程式，則此 [!DNL widget] 會顯示， **[!UICONTROL No Recommended Patches]**.

## 使用時機

此 **[!UICONTROL Dashboard]** page是您在 [!DNL Site-Wide Analysis Tool] 不僅可輕鬆檢視網站整體健康狀況的「大圖」，還可透過每個 [!DNL widget].

## 優點

* 此 [!DNL widgets] for [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]，和 [!UICONTROL Security Scan] 所有這些圖都使用易於讀取的彩色編碼互動式圓形圖，並將圖形圖例放在旁邊，然後計算中心的總計，以表示有多少個 [!UICONTROL Recommendations], [!UICONTROL Extensions]，和 [!UICONTROL Security Scan Tool] 每個功能都有的項目。 [!UICONTROL Recommendations] 和 [!UICONTROL Security Scan Tool] 圖表會依嚴重性分隔。 [!UICONTROL Extensions] 分為四個分類：當前版本、舊版本、禁用和未知。

* [!DNL New Relic Alerts] 會在頂端列出最新的警報，包括簡短說明和警報發生的時間。

* 此 [!UICONTROL Recommendations] 和 [!UICONTROL Extensions] [!DNL widgets] 按一下「 」，即可存取每個功能的完整資料頁面 **[!UICONTROL View All]**.

* 此 [!UICONTROL Security Scan Tool] 有 **[!UICONTROL View Report]** 連結 [!DNL widget] 帶你到 [!UICONTROL Recommendations] 頁面。

* 此 [!DNL Upgrade Compatibility Tool] 有 **[!UICONTROL Run Upgrade Scan]** 按鈕 [!DNL widget] 窗口。

## 使用 [!UICONTROL Dashboard]

* 按一下 [!DNL widget] 存取其提供的詳細資料，以便深入了解並了解您網站的安全性、健康狀況、建議，以及改善網站的最佳實務。

* 前往 [!UICONTROL Security Scan Tool] [!DNL widget] 按一下 [!UICONTROL View Report] 若要檢視 [!UICONTROL Recommendations] 報告。

* 使用 [!DNL External Resources] 連結可讓您了解更多資訊、掌握最新的安全性修補程式、更新和最佳實務，或善用 [Adobe Commerce幫助中心支援知識庫（幫助中心）](https://support.magento.com/), [Adobe Commerce開發人員檔案(DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [安全中心](https://helpx.adobe.com/security.html)，和 [Adobe Commerce觀察](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).
