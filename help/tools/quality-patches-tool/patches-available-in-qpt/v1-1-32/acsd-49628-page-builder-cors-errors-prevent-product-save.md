---
title: 'ACSD-49628： [!DNL Page Builder] CORS錯誤導致無法儲存產品'
description: 套用ACSD-49628修補程式以修正Adobe Commerce問題，該問題導致 [!DNL Page Builder] CORS錯誤無法儲存產品。
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628： [!DNL Page Builder] CORS錯誤導致無法儲存產品

ACSD-49628修補程式修正了[!DNL Page Builder] CORS錯誤導致管理員無法儲存產品的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-49628。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL Page Builder] CORS錯誤導致無法儲存產品。

<u>要再現的步驟</u>：

1. 以管理員身分登入。
1. 建立具有下列許可權的使用者角色：

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**。
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**。

1. 不要新增任何&#x200B;*[!UICONTROL Content]*&#x200B;許可權。
1. 建立另一個管理員使用者，並將上面建立的角色指派給此使用者。
1. 建立產品並登出。
1. 以第二個管理員身分登入。
1. 嘗試編輯並儲存產品。

<u>預期結果</u>：

第二個管理員可以儲存產品，但若無任何&#x200B;*[!UICONTROL Content]*&#x200B;許可權，**[!UICONTROL Edit with Page Builder]**&#x200B;按鈕不會顯示給管理員。

<u>實際結果</u>：

第二個管理員無法儲存產品，因為發生多個[!DNL Page Builder]錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
