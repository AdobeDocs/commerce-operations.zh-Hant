---
title: 運送地址變更時，「商店見面交收」中預先選取的商店不會更新
description: 套用ACSD-64753修補程式，修正Adobe Commerce在所選商店服務半徑以外輸入新運送地址時，預先選取商店未更新的問題。
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-64753：當送貨地址變更時，「店內取貨」中預先選取的商店不會更新

ACSD-64753修補程式修正了在所選商店服務半徑之外輸入新送貨地址時，預先選取商店未更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63時，即可使用此修補程式。 修補程式ID為ACSD-64753。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在所選商店的服務半徑之外輸入新送貨地址時，預先選取的商店未更新。

<u>要再現的步驟</u>：

1. 導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**」以啟用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 為[!DNL Google Distance Provider]提供有效的[!DNL Google] API金鑰。 若要這麼做，請導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**。
1. 新增來源(**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**)，並設定下列值：
   * **[!UICONTROL Latitude]**： *-41.917344*
   * **[!UICONTROL Longitude]**： *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**： *是*
   * **[!UICONTROL Country United]**： *狀態*
   * **[!UICONTROL State]**： *伊利諾*
   * **[!UICONTROL City]**： *Carol資料流*
   * **[!UICONTROL Postcode]**： *60188*
1. 新增庫存(**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**)，將新來源和主要網站指派給它。
1. 編輯任何產品，將產品指派給新的Source，有庫存且數量> *0*。
1. 等候重新索引完成。
1. 在店面，建立新客戶，然後新增加州地址作為預設帳單和運送。
1. 新增另一個非預設的伊利諾地址給此客戶。
1. 將產品新增到購物車並繼續結帳。
1. 保留選取的加州送貨地址，並選擇&#x200B;**[!UICONTROL Pick in Store]**&#x200B;送貨方式。 按一下&#x200B;**[!UICONTROL Next]**。

<u>預期結果</u>：

由於加州位址超出搜尋半徑上限（200公里），因此客戶不應使用Illinois Source。

<u>實際結果</u>：

您可選擇伊利諾州的貨源，然後客戶便可繼續結帳。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
