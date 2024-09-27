---
title: 「ACSD-56858：B2B公司管理員中的角色許可權不一致」
description: 套用ACSD-56858修補程式以修正B2B環境中受限制公司管理員角色許可權顯示錯誤的Adobe Commerce問題。
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56858：B2B公司管理員中的角色許可權差異

ACSD-56858修補程式修正B2B環境中受限制公司管理員的角色許可權顯示不正確的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.47時，即可使用此修補程式。 修補程式ID為ACSD-56858。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限制的公司管理員在B2B環境中的角色許可權顯示不正確。

<u>要再現的步驟</u>：

1. 首先，請設定公司、新增公司管理員和公司使用者。
1. 以店面的公司管理員身分登入，並為不同使用者建立各種角色。
1. 視需要指派這些角色，例如限制某些任務的存取權，同時允許其他任務的完全存取權。
1. 將這些角色以完整存取權指派給公司管理員以外的使用者。
1. 以非公司管理員使用者身分登入，例如company_manager。
1. 導覽至&#x200B;**[!UICONTROL Roles and permission]**&#x200B;並編輯角色。
1. 請注意，顯示的許可權與公司資料庫中針對該角色ID設定的許可權不符。

<u>預期結果</u>：

非公司管理員使用者的角色和許可權會顯示正確。

<u>實際結果</u>：

根據許可權表格中的資料庫記錄，非公司管理員使用者的角色無法正確顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
