---
title: ACSD-50813：管理員無法新增包含斜線的套件組合產品
description: 套用ACSD-50813修補程式以修正Adobe Commerce效能問題，該問題導致管理員無法透過*Add Products by SKU*功能在SKU中新增包含斜線標籤('/')的套件式產品至管理員訂單。
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813：管理員無法新增包含斜線的套件組合產品

ACSD-50813修補程式修正管理員無法在具有&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;功能的SKU中，將包含斜線標籤(`/`)的套件產品新增至管理員訂單的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-50813。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員無法在具有&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;功能的SKU中，將包含斜線標籤(`/`)的套件產品新增至管理員訂單。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 建立簡單的產品。
1. 建立新的套件產品。
1. 在SKU中間加入斜線標籤(`/`) （範例： *Bu/ndle*）。
1. 新增搭配&#x200B;**[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*&#x200B;的選項。
1. 將至少一個簡單產品指派給選項。
1. 前往&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**，並建立新訂單。
1. 按一下&#x200B;**[!UICONTROL Add Products by SKU]**。
1. 輸入您的SKU，然後按一下&#x200B;**[!UICONTROL Add to Order]**。
1. 開啟瀏覽器主控台。
1. 按一下&#x200B;**[!UICONTROL Configure]**。

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

主控台中的JS錯誤：

*未攔截到的錯誤：語法錯誤，無法辨識的運算式： div[id=sku_bu/ndle]*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
