---
title: 如何存取 [!DNL Site-Wide Analysis Tool]
description: 瞭解如何存取 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 2896442432158456698cac2d566cf0f61b5d7847
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# 如何存取[!DNL Site-Wide Analysis Tool]

您可以從商店的[!DNL Site-Wide Analysis Tool]存取[!UICONTROL Admin Panel]儀表板。

[!DNL Site-Wide Analysis Tool]服務可在[生產模式](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes)中供具有存取使用者[!UICONTROL Admin]角色資源[許可權的](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)使用者使用。

>[!NOTE]
>
>自2024年4月23日起，[!DNL Site-Wide Analysis Tool]已終止服務，不再供Adobe Commerce內部部署客戶使用。


![全網站分析儀表板](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]儀表板*

>[!NOTE]
>
>您的帳戶應有權使用&#x200B;**[!DNL Support Permissions]**&#x200B;以存取[!DNL Site-Wide Analysis Tool Dashboard]。
>>請參閱我們的使用手冊中的[共用 [!DNL Commerce] 帳戶](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html)檢視更多詳細資料。

## 從您商店的[!DNL Site-Wide Analysis Tool Dashboard]登入[!UICONTROL Admin Panel]

### 步驟1：驗證許可權

驗證[!UICONTROL Admin]使用者帳戶是否具有透過其[!DNL Site-Wide Analysis Tool]指派的使用者角色[存取](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)的許可權。

>[!IMPORTANT]
>
>[!DNL Site-Wide Analysis Tool]角色資源（許可權）是&#x200B;**非**&#x200B;自動指派。 必須針對使用者角色啟動它，且角色必須個別指派給[!UICONTROL Admin]中的每個使用者帳戶。

針對需要[!DNL Site-Wide Analysis Tool]存取權的自訂角色，請執行下列動作：

1. 選取&#x200B;**[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**&#x200B;角色資源。

   ![全網站分析儀表板](../../assets/tools/swat-role-access.png)
   已為角色&#x200B;*[!DNL Site-Wide Analysis Tool]選取*&#x200B;許可權

1. 按一下&#x200B;**[!UICONTROL Save Role]**。

1. 通知所有被指派該角色的使用者登出[!DNL Admin]，然後重新登入。

>[!NOTE]
>
>如果您已驗證使用者帳戶具有存取[!DNL Site-Wide Analysis Tool]的許可權，且使用者嘗試從[!UICONTROL Admin]存取工具時收到403錯誤，則您在雲端基礎結構上的Adobe Commerce執行個體可能已啟用HTTP存取控制。 如果您已啟用HTTP驗證，則不支援[!DNL Site-Wide Analysis Tool]儀表板。 如需解決此問題的詳細資訊，請參閱我們的[支援文章](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento)。

### 步驟2：存取[!DNL Site-Wide Analysis Tool]

1. 在&#x200B;*[!UICONTROL Admin]*&#x200B;側邊欄上，前往&#x200B;**[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**。

   ![全網站分析儀表板](../../assets/tools/ac-admin-panel-marked.jpg)
   在Adobe Commerce *[!DNL Site-Wide Analysis Tool]的[!UICONTROL Admin Panel]中的*&#x200B;位置

1. 閱讀&#x200B;*的*&#x200B;使用條款[!DNL Site-Wide Analysis Tool]並按一下&#x200B;**[!UICONTROL Accept]**&#x200B;以繼續。

   每位使用者都必須接受工作階段的使用條款。 此步驟會針對每個登入工作階段重複執行。


1. 在控制面板頂端，按一下您要檢視的標籤。

   ![全網站分析儀表板](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]資訊*

## 從[!DNL Site-Wide Analysis Tool Dashboard]產生報告

1. 按一下控制面板右上角的&#x200B;**[!UICONTROL Generate Report]**。

1. 針對您要在報告中包含的每個&#x200B;**[!UICONTROL Type]**&#x200B;和&#x200B;**[!UICONTROL Priority]**&#x200B;設定選取核取方塊。

1. 按一下&#x200B;**[!UICONTROL Generate Report]**。

   ![全網站分析儀表板](../../assets/tools/swat-report-settings.png)
   *報告設定*

| 標籤 | 說明 |
| --- | --- |
| 儀表板 | 依優先順序顯示目前通知和建議的系統健康情況。 |
| 資訊 | 提供客戶連絡資訊和目前票證的摘要，以及有關每個已安裝Adobe Commerce產品的詳細資訊。 |
| Recommendations | 根據最佳做法列出建議，以解決在您的網站上偵測到的問題。 |
| 例外 | 列出應用程式因無錯誤處理常式的異常狀況所引發的錯誤。 |
| 擴充功能 | 列出所有協力廠商擴充功能和協力廠商程式庫。 |

>[!NOTE]
>
>套用建議後，可能需要幾天時間才能在[!DNL Site-Wide Analysis Tool Dashboard]或產生的報表中更新。
