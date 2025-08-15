---
title: ACSD-65331：回到結帳後，[!UICONTROL Pick in Store]中選取的存放區已清除
description: 套用ACSD-65331修補程式以修正Adobe Commerce問題，該問題導致使用者重複返回結帳頁面時，[!UICONTROL Pick In Store]選項下選取的存放區遭到清除。
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331：回到結帳後，**[!UICONTROL Pick in Store]**&#x200B;中選取的存放區已清除

ACSD-65331修補程式修正使用者重複返回結帳頁面時，**[!UICONTROL Pick In Store]**&#x200B;選項下選取的存放區被清除的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-65331。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者重複回到結帳頁面時，**[!UICONTROL Pick In Store]**&#x200B;選項下選取的存放區會被清除。

<u>要再現的步驟</u>：

1. 導覽至「**[!UICONTROL In-Store Delivery]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**」以啟用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 導覽至[!DNL Google] > [!UICONTROL Google Distance Provider] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**，設定&#x200B;**[!UICONTROL Inventory]**&#x200B;的有效&#x200B;**[!UICONTROL Google Distance Provider]** API金鑰。
1. 移至「**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**」以新增包含下列詳細資訊的來源：

   * **[!UICONTROL Latitude]**： *41.917344*
   * **[!UICONTROL Longitude]**： *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**： *是*
   * **[!UICONTROL Country]**： *美國*
   * **[!UICONTROL State]**： *伊利諾*
   * **[!UICONTROL City]**： *Carol資料流*
   * **[!UICONTROL Street]**： *E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**： *60188*

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]**」以建立新庫存。

   將新建立的來源和主要網站指派給此庫存。
1. 編輯任何產品並：

   1. 將其指派給新建立的來源。
   1. 將其狀態設定為&#x200B;*[!UICONTROL In Stock]*，並將數量設定為大於0。

1. 執行您的索引子。
1. 在店面，建立新客戶並將加州地址設定為預設帳單和送貨地址。
1. 新增其他伊利諾地址給同一個客戶（非預設）。
1. 將已設定的產品新增到購物車並繼續前往&#x200B;**[!UICONTROL Checkout]**。
1. 選取伊利諾地址，選擇&#x200B;**[!UICONTROL Pick In Store]**&#x200B;作為送貨方法，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 等候來源載入，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 導覽回首頁。
1. 重新造訪&#x200B;**[!UICONTROL Checkout]**&#x200B;頁面。

<u>預期結果</u>：

選取的存放區應在&#x200B;**[!UICONTROL Pick In Store]**&#x200B;下保持可用。

<u>實際結果</u>：

出貨步驟開始載入並重新導向至&#x200B;**[!UICONTROL Pick In Store]**，但看不到任何商店。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
