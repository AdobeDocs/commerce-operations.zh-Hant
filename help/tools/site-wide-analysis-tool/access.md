---
title: 如何訪問 [!DNL Site-Wide Analysis Tool]
description: 瞭解如何訪問 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 如何訪問 [!DNL Site-Wide Analysis Tool]

的 [!DNL Site-Wide Analysis Tool] 服務可在 [生產模式](https://docs.magento.com/user-guide/magento/installation-modes.html) 為 [!DNL Admin] 具有訪問用戶權限的用戶 [角色資源](https://docs.magento.com/user-guide/system/permissions-user-roles.html)。

>[!NOTE]
>
>如果您在本地安裝了Adobe Commerce，則必須安裝 [代理](../site-wide-analysis-tool/installation.md) 以使用該工具。

![站點範圍分析儀表板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]儀表板*

## 步驟1:驗證權限

驗證 [!DNL Admin] 用戶帳戶具有訪問權限 [!DNL Site-Wide Analysis Tool] 通過 [已分配用戶角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html)。

>[!IMPORTANT]
>
>的 [!DNL Site-Wide Analysis Tool] 角色資源（權限）為 **不** 自動分配。 必須為中的每個用戶帳戶分別分配的用戶角色和角色激活該角色 [!UICONTROL Admin]。

對於需要的自定義角色 [!DNL Site-Wide Analysis Tool] 訪問，執行以下操作：

1. 選擇 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 角色資源。

   ![站點範圍分析儀表板](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]為角色選擇的權限*

1. 按一下 **[!UICONTROL Save Role]**。

1. 通知分配了該角色的所有用戶註銷 [!DNL Admin]，並再次登錄。

>[!NOTE]
>
>如果您已驗證用戶帳戶有權訪問 [!DNL Site-Wide Analysis Tool] 用戶在嘗試從 [!DNL Admin]，您在雲基礎架構上的Adobe Commerce實例可以啟用HTTP訪問控制。 的 [!DNL Site-Wide Analysis Tool] 如果啟用了HTTP身份驗證，則不支援儀表板。 有關解決此問題的詳細資訊，請參閱 [支援文章](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671)。

## 步驟2:訪問 [!DNL Site-Wide Analysis Tool]

1. 在 *[!UICONTROL Admin]* 邊欄，轉到 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**。

1. 閱讀 *使用條款* 為 [!DNL Site-Wide Analysis Tool] 按一下 **[!UICONTROL Accept]** 繼續。

   每個用戶都必須接受會話的使用條款。 對每個登錄會話重複此步驟。

   ![站點範圍分析儀表板](../../assets/tools/swat-tos.png)
   *使用條款*

1. 在儀表板頂部，按一下要查看的頁籤。

   ![站點範圍分析儀表板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]資訊*

## 第3步：生成報告

1. 在操控板的右上角，按一下 **[!UICONTROL Generate Report]**。

1. 選中每個選項的複選框 **[!UICONTROL Type]** 和 **[!UICONTROL Priority]** 的子菜單。

1. 按一下 **[!UICONTROL Generate Report]**。

   ![站點範圍分析儀表板](../../assets/tools/swat-report-settings.png)
   *報告設定*

| 頁籤 | 說明 |
| --- | --- |
| 儀表板 | 按優先順序顯示當前通知和建議的系統運行狀況。 |
| 資訊 | 提供客戶聯繫資訊和當前票證的摘要，以及有關每個已安裝的Adobe Commerce產品的詳細資訊。 |
| Recommendations | 根據最佳實踐列出建議，以解決您站點上檢測到的問題。 |
| 例外 | 列出應用程式拋出的錯誤，這些錯誤是由沒有錯誤處理程式的異常情況引起的。 |
| 擴展 | 列出所有第三方擴展和第三方庫。 |

>[!NOTE]
>
>在應用建議後，可能需要幾天時間才能在 [!DNL Site-Wide Analysis Tool] 儀表板或生成的報表。
