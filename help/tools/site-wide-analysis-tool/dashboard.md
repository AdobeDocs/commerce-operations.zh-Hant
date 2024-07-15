---
title: '[!DNL Dashboard]'
description: 瞭解 [!DNL Site-Wide Analysis Tool]元素中的 [!DNL Dashboard] 標籤、使用時機、優點及最佳實務。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

[!UICONTROL Dashboard]頁面顯示一覽[!DNL widgets]，其中提供您Adobe Commerce網站運作狀態與目前狀態的「單一窗格」。 每個[!DNL widget]都包含每個功能頁面、每個工具本身或報告的存取連結（視[!DNL widget]而定）。
另外還有[!UICONTROL External Resources]個Adobe Commerce連結清單，包括[Adobe Commerce說明中心支援知識庫（說明中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)、[Adobe Commerce開發人員檔案(DevDocs)](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、[安全性中心](https://helpx.adobe.com/security.html)以及[Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)的觀察。

## 元素

* **[!UICONTROL Recommendations]**：顯示您網站的最佳實務建議。 Recommendations （發現的問題和要修正的建議）會依優先順序排序 — P0 （嚴重）到P4 （通知）。
Recommendations包含說明、建議、網站影響、根本原因、案例/先決條件，以及使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**：分析安裝在Adobe Commerce自訂執行個體中的所有模組和核心程式碼，以針對特定版本檢查該執行個體。 它會傳回在升級至最新版Adobe Commerce之前必須解決的嚴重問題、錯誤和警告清單。 它也會識別在嘗試升級至較新版本的Adobe Commerce之前，必須在程式碼中修正的潛在問題。
[!UICONTROL Upgrade Compatibility Tool]可讓您識別自訂功能何時進行核心程式碼變更。

* **[!UICONTROL Security Center Widget]**：顯示您網站的安全性深入分析。
顯示的安全性資訊包含[技術 [!DNL Stack] 版本相容性與 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 最佳實務安全性Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)。<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)會監視Adobe Commerce網站的安全性風險。 它可以主動且有效率地偵測商戶商店中的惡意程式，並在發生任何安全性風險、惡意程式碼或威脅時通知商家，還可以識別遺失的Adobe Commerce修補程式和更新。

* **[!UICONTROL Extensions]**：顯示目前安裝在您Adobe Commerce執行個體的擴充功能。 [已提供Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html)資訊（如果有的話），適用於此處列出的擴充功能。

* **[!UICONTROL Alerts]**：顯示Adobe Commerce執行個體最新的[!DNL New Relic Managed Alerts]。 在Adobe Commerce支援知識庫中進一步瞭解[Adobe Commerce受管理警示](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html)以及如何[存取New Relic服務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html)。

* **[!UICONTROL Non-recommended software in use]**：根據您的Adobe Commerce版本，顯示您的Adobe Commerce執行個體目前使用的非建議軟體。 不建議的軟體由[!UICONTROL Name]、[!UICONTROL Installed Version]和[!UICONTROL Recommended Version]列出。

* **[!UICONTROL Recommended Patches]**：根據您可能已安裝之修補程式和Adobe Commerce版本，顯示任何建議修補程式的簡短清單。 建議修補程式的完整清單可在&#x200B;**[!UICONTROL Patches]**&#x200B;功能標籤中找到，該標籤也位於[!DNL Site-Wide Analysis Tool]內。 修補程式由[[!DNL Quality Patches Tool]提供：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 列出的所有修補程式都與您目前的Adobe Commerce執行個體相容。
如果沒有建議為您的Adobe Commerce執行個體顯示的修補程式，則會顯示此[!DNL widget] **[!UICONTROL No Recommended Patches]**。

## 使用時機

**[!UICONTROL Dashboard]**&#x200B;頁面是您在[!DNL Site-Wide Analysis Tool]中的總覽式命令中心，不僅可輕鬆檢視您網站整體健康情況的「概觀」，您還可以透過每個[!DNL widget]檢視和存取您Adobe Commerce網站的特定工具、建議和報告。

## 優點

* [!UICONTROL Security Center]、[!UICONTROL Recommendations]、[!UICONTROL Extensions]和[!UICONTROL Security Scan]的[!DNL widgets]都使用易於閱讀的以色彩編碼的互動圓形圖形，圖形圖例位於旁邊，並以中心點計數總計，表示每個功能有[!UICONTROL Recommendations]、[!UICONTROL Extensions]和[!UICONTROL Security Scan Tool]個專案。 [!UICONTROL Recommendations]和[!UICONTROL Security Scan Tool]圖表以嚴重程度分隔。 [!UICONTROL Extensions]分為四個分類：目前版本、舊版本、已停用和未知。

* [!DNL New Relic Alerts]列在最上面，包含簡短說明以及警報發生的時間。

* [!UICONTROL Recommendations]與[!UICONTROL Extensions] [!DNL widgets]可以按一下「**[!UICONTROL View All]**」來存取每個功能的完整資料頁。

* [!UICONTROL Security Scan Tool]在[!DNL widget]視窗中有&#x200B;**[!UICONTROL View Report]**&#x200B;連結，可帶您前往[!UICONTROL Recommendations]頁面。

* [!DNL Upgrade Compatibility Tool]在[!DNL widget]視窗中有&#x200B;**[!UICONTROL Run Upgrade Scan]**&#x200B;按鈕。

## 使用[!UICONTROL Dashboard]的最佳實務

* 按一下每個[!DNL widget]，存取其提供的詳細資料，以深入瞭解並瞭解您網站的安全性、健康狀態、建議和最佳實務，進而改善網站。

* 移至[!UICONTROL Security Scan Tool] [!DNL widget]並按一下[!UICONTROL View Report]以檢視您網站的[!UICONTROL Recommendations]報告。

* 使用[!DNL External Resources]連結來瞭解詳細資訊、持續瞭解安全性修補程式、更新及最佳實務，或利用[Adobe Commerce說明中心支援知識庫（說明中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)、[Adobe Commerce開發人員檔案(DevDocs)](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、[安全性中心](https://helpx.adobe.com/security.html)以及[Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)的觀察。
