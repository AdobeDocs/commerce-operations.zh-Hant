---
title: 如何存取 [!DNL Site-Wide Analysis Tool]
description: 瞭解如何存取 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# 如何存取 [!DNL Site-Wide Analysis Tool]

您可透過兩種方式存取 [!DNL Site-Wide Analysis Tool Dashboard].

您可以存取 [!DNL dashboard] 從 [[!DNL Site-Wide Analysis Tool] 網站](https://supportinsights.adobe.com/commerce) 直接 **(僅適用於雲端基礎結構上的Adobe Commerce)** 並登入Adobe ID，或透過以下方式存取： [!DNL dashboard] 來自您商店的 [!DNL Admin Panel].

此 [!DNL Site-Wide Analysis Tool] 服務適用於 [生產模式](https://docs.magento.com/user-guide/magento/installation-modes.html) 的 [!DNL Admin] 具有存取使用者許可權的使用者 [角色資源](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>如果您內部部署已安裝Adobe Commerce，則必須安裝 [代理程式](../site-wide-analysis-tool/installation.md) ，以使用此工具。

![全網站分析控制面板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]儀表板*

## 選項1：登入您的 [!DNL Site-Wide Analysis Tool Dashboard] 直接從 [!DNL Site-Wide Analysis Tool] 網域(僅適用於雲端基礎結構上的Adobe Commerce)

一個 **[!DNL Adobe ID]為必要項** 存取 [!DNL Commerce] 帳戶。
如果您已有 [!DNL Commerce] 帳戶，但您沒有 [!DNL Adobe ID]，您可在登入過程中建立一個。

1. 前往 [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. 按一下 **[!UICONTROL Sign in with Adobe ID]** 按鈕並依照提示操作。

   ![全網站分析控制面板](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]登入畫面*

1. 接受條款與條件。

1. **<u>注意</u>：** 您的帳戶應有權使用 **[!DNL Support Permissions]** 以存取 [!DNL Site-Wide Analysis Tool Dashboard].
如需詳細資訊，請參閱 [共用 [!DNL Commerce] 帳戶](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) 在我們的使用手冊中。

## 選項2：登入您的 [!DNL Site-Wide Analysis Tool Dashboard] 來自您商店的 [!DNL Admin Panel]

### 步驟1：驗證許可權

確認 [!DNL Admin] 使用者帳戶具有存取 [!DNL Site-Wide Analysis Tool] 透過其 [已指派的使用者角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>此 [!DNL Site-Wide Analysis Tool] 角色資源（許可權）為 **非** 自動指派。 必須為使用者角色以及單獨指派給中每個使用者帳戶的角色啟用 [!UICONTROL Admin].

對於需要的自訂角色 [!DNL Site-Wide Analysis Tool] 存取，請執行以下操作：

1. 選取 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 角色資源。

   ![全網站分析控制面板](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]為角色選取的許可權*

1. 按一下 **[!UICONTROL Save Role]**.

1. 通知任何獲指派該角色的使用者登出 [!DNL Admin]，然後重新登入。

>[!NOTE]
>
>如果您已驗證使用者帳戶具有存取 [!DNL Site-Wide Analysis Tool] 而使用者嘗試從存取工具時收到403錯誤 [!DNL Admin]，您雲端基礎結構上的Adobe Commerce執行個體可能會啟用HTTP存取控制。 此 [!DNL Site-Wide Analysis Tool] 如果您已啟用HTTP驗證，則儀表板不受支援。 如需解決此問題的詳細資訊，請參閱我們的 [支援文章](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### 步驟2：存取 [!DNL Site-Wide Analysis Tool]

1. 在 *[!UICONTROL Admin]* 側欄，前往 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![全網站分析控制面板](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]中的位置 [!DNL Admin Panel] 在Adobe Commerce中*

1. 閱讀 *使用條款* 針對 [!DNL Site-Wide Analysis Tool] 並按一下 **[!UICONTROL Accept]** 以繼續。

   每位使用者都必須接受工作階段的使用條款。 此步驟會針對每個登入工作階段重複執行。


1. 在控制面板頂端，按一下您要檢視的標籤。

   ![全網站分析控制面板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]資訊*

## 從產生報表 [!DNL Site-Wide Analysis Tool Dashboard]

1. 在控制面板的右上角，按一下 **[!UICONTROL Generate Report]**.

1. 勾選每個的核取方塊 **[!UICONTROL Type]** 和 **[!UICONTROL Priority]** 要納入報表中的設定。

1. 按一下 **[!UICONTROL Generate Report]**.

   ![全網站分析控制面板](../../assets/tools/swat-report-settings.png)
   *報表設定*

| 標籤 | 說明 |
| --- | --- |
| 儀表板 | 依優先順序顯示目前通知和建議的系統健康情況。 |
| 資訊 | 提供客戶連絡資訊和目前票證的摘要，以及有關每個已安裝Adobe Commerce產品的詳細資訊。 |
| Recommendations | 根據最佳做法列出建議，以解決在您的網站上偵測到的問題。 |
| 例外 | 列出應用程式因無錯誤處理常式的異常狀況所引發的錯誤。 |
| 擴充功能 | 列出所有協力廠商擴充功能和協力廠商程式庫。 |

>[!NOTE]
>
>套用建議後，可能需要幾天時間才能在 [!DNL Site-Wide Analysis Tool Dashboard] 或產生的報表。
