---
title: ACSD-48164：受限制的管理員無法儲存網站層級的值
description: 套用ACSD-48164修補程式以修正受限管理員無法儲存網站層級值的Adobe Commerce問題。
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164：受限制的管理員無法儲存網站層級的值

ACSD-48164修補程式修正受限管理員無法儲存網站層級值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48164。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限管理員無法儲存網站層級的值。

<u>要再現的步驟</u>：

1. 在[!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**&#x200B;中建立新網站、商店和商店檢視。
1. 在[!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**&#x200B;中建立新的管理員角色。

   * 移至&#x200B;**[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**，選取新網站，然後將此角色指派給任何管理員使用者。

1. 選取任何產品並僅指派新網站。 請勿選取預設網站。
1. 以步驟2中指派的管理員使用者身分登入，並透過變更任何網站層級屬性（如&#x200B;*[!UICONTROL Status]*、*[!UICONTROL Tax Class]*）來編輯&#x200B;**[!UICONTROL All Store View]**&#x200B;範圍下的產品，然後將產品設定為新產品。
1. 儲存產品。

<u>預期結果</u>：

與角色範圍關聯至一個網站的管理員使用者可以使用&#x200B;*[!UICONTROL All Store View]*&#x200B;範圍儲存網站層級產品屬性。

<u>實際結果</u>：

產品已儲存的成功訊息隨即顯示，但產品屬性值保持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
