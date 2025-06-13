---
title: ACSD-49748：無法傳送電子郵件邀請
description: 套用ACSD-49748修補程式以修正使用者無法傳送電子郵件邀請的Adobe Commerce問題。
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
exl-id: 03dad66c-4691-421e-8c80-eca12c60175c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# ACSD-49748：無法傳送電子郵件邀請

ACSD-49748修補程式修正使用者無法傳送電子郵件邀請的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49748。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤&#x200B;*傳送邀請時發生錯誤*&#x200B;在傳送邀請時出現。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**」。
1. 建立邀請並儲存。
1. 移至&#x200B;**[!UICONTROL Invitation Grid]**&#x200B;並選取任何邀請。
1. 傳送邀請。

<u>預期結果</u>：

按一下「*[!UICONTROL Send Invitation]*」時會傳送邀請。

<u>實際結果</u>：

錯誤&#x200B;*傳送邀請時發生錯誤*，邀請未傳送。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。
