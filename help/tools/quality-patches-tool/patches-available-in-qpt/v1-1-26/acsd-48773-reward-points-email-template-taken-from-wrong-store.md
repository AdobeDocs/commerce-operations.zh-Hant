---
title: 'ACSD-48773：從錯誤的商店取得的獎勵點數電子郵件範本'
description: 套用ACSD-48773修補程式，修正從錯誤商店取得獎勵點數電子郵件範本的Adobe Commerce問題。
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773：從錯誤的商店取得的獎勵點數電子郵件範本

ACSD-48773修補程式修正了從錯誤商店取得獎勵點電子郵件範本的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48773。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果套件組合產品未指派給任何網站，則產品價格重新指數無法運作。

<u>要再現的步驟</u>：

1. 建立2個網站、2個商店和2個商店檢視。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]**」並啟用&#x200B;**[!UICONTROL Reviews]**。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**。
切換至**[!DNL default website scope]**，並設定&#x200B;**[!UICONTROL Customer Support Sender Email]**&#x200B;位址(例如： *support_base@example.com*)。
切換至**[!DNL second website scope]**，並將&#x200B;**[!UICONTROL Customer Support Sender Email]**&#x200B;位址設定為另一個值(例如： *support_second@example.com*)。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**，並設定&#x200B;**[!UICONTROL Share Customer Accounts]** = *每個網站*。
1. 在&#x200B;**[!UICONTROL Reward Points]**底下，設定下列專案：
   **[!UICONTROL Enable Reward Points Functionality]** = *是*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *是*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]**&#x200B;並設定&#x200B;**[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]**&#x200B;並設定&#x200B;**[!UICONTROL Email Sender]** = *客戶支援*
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**，並為&#x200B;**[!UICONTROL Points/Currency]**&#x200B;和&#x200B;**[!UICONTROL Currency/Points]**&#x200B;設定第二個網站的匯率。
1. 在第二個網站上建立客戶帳戶。
1. 以客戶身分登入第二個網站。
1. 請確定啟用&#x200B;**[!UICONTROL Balance Updates]**&#x200B;的&#x200B;**[!UICONTROL Subscribe]**。
1. 提交產品評論。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**。
1. 將新稽核的狀態變更為&#x200B;***[!UICONTROL Approved]***&#x200B;和&#x200B;**[!UICONTROL Save]**。
1. 等候電子郵件送達。

<u>預期結果</u>：

第二個網站範圍上設定的電子郵件寄件者應該已傳送獎勵點數更新電子郵件。

<u>實際結果</u>：

預設網站範圍上設定的電子郵件寄件者已傳送獎勵點數更新電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
