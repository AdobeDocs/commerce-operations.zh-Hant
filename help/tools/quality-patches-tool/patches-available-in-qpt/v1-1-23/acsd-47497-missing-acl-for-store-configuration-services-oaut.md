---
title: 'ACSD-47497：遺失存放區/設定/服務[!UICONTROL OAuth]的ACL'
description: 為特定角色設定了許可權，而您無法定義設定區段的存取權時，請套用ACSD-47497修補程式以修正Adobe Commerce問題。
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-47497：遺失存放區/設定/服務[!UICONTROL OAuth]的ACL

ACSD-47497修補程式解決了Adobe Commerce管理員的&#x200B;**[!UICONTROL Configuration]**&#x200B;區段中看不到&#x200B;**[!UICONTROL Services]**&#x200B;標籤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23時，即可使用此修補程式。 修補程式ID為ACSD-47497。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

為特定角色設定許可權時，您無法定義&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;的存取權。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員。 前往&#x200B;**[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**。
1. 在Administrators角色中選取&#x200B;**[!UICONTROL Role Resources]**，並將&#x200B;**[!UICONTROL Roles Resources]**&#x200B;下的&#x200B;**[!UICONTROL Resource Access]**&#x200B;設定為&#x200B;_自訂_，然後選取所有核取方塊。 選取&#x200B;**[!UICONTROL Save Role]**。
1. 選取&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**。 **[!UICONTROL OAuth]**&#x200B;設定區段無法使用。

<u>預期結果</u>：

在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;中，會顯示設定區段。

<u>實際結果</u>：

在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;中，缺少設定區段。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
