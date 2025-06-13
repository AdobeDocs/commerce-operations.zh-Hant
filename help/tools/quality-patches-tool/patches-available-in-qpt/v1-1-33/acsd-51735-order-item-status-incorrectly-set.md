---
title: ACSD-51735：當產品庫存為0時，訂單專案狀態錯誤地設定為*[!UICONTROL Ordered]*
description: 套用ACSD-51735修補程式，修正產品庫存為0時，訂單專案狀態未正確設定為*[!UICONTROL Ordered]*的Adobe Commerce問題。
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735：產品庫存為0時，訂單專案狀態未正確設定為&#x200B;*[!UICONTROL Ordered]*

ACSD-51735修補程式修正產品庫存為0時，訂單專案狀態未正確設定為&#x200B;*[!UICONTROL Ordered]*&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-50895。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當產品庫存為0時，訂單專案狀態錯誤地設定為&#x200B;*[!UICONTROL Ordered]*。

<u>必要條件</u>：

* Adobe Commerce Inventory management (MSI)模組已安裝。
* 延交訂單已在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**&#x200B;中啟用。

<u>要再現的步驟</u>：

1. 建立新庫存。
1. 建立新的來源。
1. 將預設網站指派給新庫存，並指派新來源。
1. 建立新產品。

   * 將預設來源數量設為10，並將新來源數量設為0。

1. 將產品新增至店面的購物車。
1. 觀察結帳時的延期交貨警告，指出產品來自新來源。
1. 下訂單。
1. 在「管理員」中開啟訂單，並檢查延期交貨狀態。

<u>預期結果</u>：

訂單顯示「數量1」已延交。

<u>實際結果</u>：

訂單顯示Qty 1已訂購，而非延交。

>[!MORELIKETHIS]
>
>[訂單專案狀態未正確設定為&#x200B;*[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
