---
title: 'ACSD-56621：更新後的名稱未顯示在公司管理員使用者的問候語標題中'
description: 套用ACSD-56621修補程式以修正Adobe Commerce問題，該問題導致更新後的公司管理員使用者名字和姓氏未反映在問候語標題區段中。
feature: Companies, B2B, User Account
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621：更新後的名稱未顯示在公司管理員使用者的問候語標題中

ACSD-56621修補程式修正了Greetings標頭區段中未反映公司管理員使用者更新名字和姓氏的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46時，即可使用此修補程式。 修補程式ID為ACSD-56621。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新的名稱不會顯示在公司管理員使用者的問候語標題中。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
1. 移至&#x200B;**[!UICONTROL Stores]**&#x200B;並選取&#x200B;**[!UICONTROL Configuration]**。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;區段下，選取&#x200B;**[!UICONTROL B2B]**&#x200B;以啟用B2B公司功能。
1. 移至&#x200B;**[!UICONTROL Storefront]**&#x200B;並註冊新公司。
1. 以公司管理員使用者身分登入。
1. 移至&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Company Users]**，並視需要修改名字和姓氏欄位。

<u>預期結果</u>：

問候語標題區段中使用者的名字和姓氏會立即變更。

<u>實際結果</u>：

使用者的名字和姓氏只有在使用者登出並再次登入時才會變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
