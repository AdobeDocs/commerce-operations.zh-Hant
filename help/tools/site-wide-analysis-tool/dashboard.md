---
title: '[!DNL Dashboard]'
description: 瞭解 [!DNL Dashboard] 的 [!DNL Site-Wide Analysis Tool]、元素、使用時間、優勢和最佳做法。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

的 [!UICONTROL Dashboard] 頁面顯示概覽 [!DNL widgets] 提供Adobe Commerce網站健康狀況和當前狀態的「單一窗格」。 每個 [!DNL widget] 包含指向每個功能頁面、每個工具本身或報告(取決於 [!DNL widget])。
還有一份 [!UICONTROL External Resources] Adobe Commerce的連結，包括 [Adobe Commerce幫助中心支援知識庫（幫助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)。 [Adobe Commerce開發人員文檔(DevDocs)](https://developer.adobe.com/commerce/docs/)。 [[!DNL Quality Patches Tool]:搜索修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 [安全中心](https://helpx.adobe.com/security.html), [Adobe Commerce觀察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)。

## 元素

* **[!UICONTROL Recommendations]**:顯示站點的最佳實踐建議。 Recommendations（發現的問題和要解決的建議）按優先順序排序 — P0（關鍵）到P4（通知）。
Recommendations包括說明、建議、站點影響、根本原因、方案/先決條件和使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**:通過分析Adobe Commerce定制實例中安裝的所有模組和核心代碼，針對特定版本檢查該實例。 它返回一列重要問題、錯誤和警告，在升級到最新版本的Adobe Commerce之前必須解決這些問題。 它還會發現在嘗試升級到較新版本的Adobe Commerce之前，必須在代碼中修復的潛在問題。
的 [!UICONTROL Upgrade Compatibility Tool] 允許您確定何時對自定義功能進行了核心代碼更改。

* **[!UICONTROL Security Center Widget]**:顯示您站點的安全見解。
所顯示的安全資訊包括 [技術 [!DNL Stack] 版本符合性 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 最佳實踐安全性Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)。<br>
的 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) 監控Adobe Commerce站點的安全風險。 它可以主動、高效地檢測商家商店上的惡意軟體，並在存在任何安全風險、惡意軟體或威脅時通知商家，並可以識別缺少的Adobe Commerce補丁程式和更新。

* **[!UICONTROL Extensions]**:顯示當前安裝在Adobe Commerce實例上的擴展。 [Adobe Commerce市場](https://marketplace.magento.com/extensions.html) 如果有，將為此處列出的擴展提供資訊。

* **[!UICONTROL Alerts]**:顯示最新 [!DNL New Relic Managed Alerts] 比如Adobe Commerce案。 瞭解有關 [針對Adobe Commerce的托管警報](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) 以及如何 [訪問New Relic服務](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) 在Adobe Commerce支援知識庫中。

* **[!UICONTROL Non-recommended software in use]**:根據您的Adobe Commerce版本顯示您的Adobe Commerce實例當前使用的非推薦軟體。 非推薦軟體由 [!UICONTROL Name]。 [!UICONTROL Installed Version], [!UICONTROL Recommended Version]。

* **[!UICONTROL Recommended Patches]**:根據您可能已安裝的修補程式和您的Adobe Commerce版本顯示任何建議的修補程式的簡短清單。 建議的修補程式的完整清單位於 **[!UICONTROL Patches]** 功能頁籤， [!DNL Site-Wide Analysis Tool]。 修補程式由 [[!DNL Quality Patches Tool]:搜索修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 列出的所有修補程式都與您當前的Adobe Commerce實例相容。
如果沒有建議為您的Adobe Commerce實例顯示的修補程式，則 [!DNL widget] 將顯示， **[!UICONTROL No Recommended Patches]**。

## 何時使用

的 **[!UICONTROL Dashboard]** 頁面是您在 [!DNL Site-Wide Analysis Tool] 不僅可以輕鬆查看您網站整體健康狀況的「大圖」，而且您還可以通過每個網站查看和訪問您Adobe Commerce網站的特定工具、建議和報告 [!DNL widget]。

## 好處

* 的 [!DNL widgets] 為 [!UICONTROL Security Center]。 [!UICONTROL Recommendations]。 [!UICONTROL Extensions], [!UICONTROL Security Scan] 全部使用易於讀取的彩色編碼互動式圓形圖，其中側面帶有圖例圖例，中心為總計，以表示有多少 [!UICONTROL Recommendations]。 [!UICONTROL Extensions], [!UICONTROL Security Scan Tool] 每個功能都包含的項目。 [!UICONTROL Recommendations] 和 [!UICONTROL Security Scan Tool] 圖表按嚴重性分隔。 [!UICONTROL Extensions] 分為四類：當前版本、舊版本、已禁用和未知。

* [!DNL New Relic Alerts] 列出了最新警報，包括簡短描述和警報發生的時間。

* 的 [!UICONTROL Recommendations] 和 [!UICONTROL Extensions] [!DNL widgets] 通過按一下 **[!UICONTROL View All]**。

* 的 [!UICONTROL Security Scan Tool] 有 **[!UICONTROL View Report]** 連結 [!DNL widget] 一扇窗 [!UICONTROL Recommendations] 的子菜單。

* 的 [!DNL Upgrade Compatibility Tool] 有 **[!UICONTROL Run Upgrade Scan]** 按鈕 [!DNL widget] 的子菜單。

## 使用 [!UICONTROL Dashboard]

* 按一下每個 [!DNL widget] 訪問它提供的詳細資料，以便深入瞭解和瞭解您網站的安全性、運行狀況、建議和最佳實踐以改進它。

* 轉到 [!UICONTROL Security Scan Tool] [!DNL widget] 按一下 [!UICONTROL View Report] 查看 [!UICONTROL Recommendations] 報告您的站點。

* 使用 [!DNL External Resources] 連結，可以瞭解更多資訊、瞭解最新的安全修補程式、更新和最佳做法，或利用 [Adobe Commerce幫助中心支援知識庫（幫助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)。 [Adobe Commerce開發人員文檔(DevDocs)](https://developer.adobe.com/commerce/docs/)。 [[!DNL Quality Patches Tool]:搜索修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 [安全中心](https://helpx.adobe.com/security.html), [Adobe Commerce觀察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)。
