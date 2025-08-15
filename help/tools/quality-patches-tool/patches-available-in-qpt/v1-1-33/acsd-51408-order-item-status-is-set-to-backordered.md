---
title: ACSD-51408：訂單專案狀態未正確設定為[!UICONTROL backordered]
description: 套用ACSD-51408修補程式以修正訂單專案狀態錯誤設定為[!UICONTROL backordered]的Adobe Commerce問題。
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408：訂單專案狀態未正確設定為&#x200B;*[!UICONTROL backordered]*

ACSD-51408修補程式修正了訂單專案狀態錯誤設定為[!UICONTROL backordered]的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51408。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單專案狀態未正確設定為&#x200B;*[!UICONTROL backordered]*。

<u>必要條件</u>：

Adobe Commerce B2B和Inventory management (MSI)模組已安裝。

<u>要再現的步驟</u>：

1. 建立新網站、商店和商店檢視。
1. 建立新的來源。
1. 建立連結至在步驟1中建立的新網站的新庫存，並指派在步驟2中建立的來源。
1. 建立公司並將其指派給在步驟1中建立的新網站。
1. 建立新客戶並將其指派給在步驟4中建立的公司。
1. 建立產品，將其指派給新網站，並將&#x200B;**[!UICONTROL default stock]** = *0*&#x200B;和&#x200B;**[!UICONTROL new stock]**&#x200B;設定為大於&#x200B;*0*。
1. 啟用&#x200B;**[!UICONTROL backorders]**。
1. 啟用新網站範圍的&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;付款方式。
1. 為新網站範圍啟用&#x200B;**[!UICONTROL Flat Rate shipping method]**。
1. 從&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**&#x200B;建立新訂單。
1. 選取在步驟5建立的新客戶。
1. 選取在步驟1建立的新商店。
1. 選擇在步驟6中建立的產品。
1. 填寫訂單資訊，包括付款和送貨方式。
1. 提交訂單。
1. 檢查&#x200B;*專案狀態*。

<u>預期結果</u>

料號可從存貨出貨。 專案狀態為&#x200B;*[!UICONTROL ordered]*。

<u>實際結果</u>

專案狀態為&#x200B;*[!UICONTROL backordered]*。

>[!MORELIKETHIS]
>
>當產品庫存為0時，[訂單專案狀態錯誤地設定為&#x200B;*[!UICONTROL Ordered]*。](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
