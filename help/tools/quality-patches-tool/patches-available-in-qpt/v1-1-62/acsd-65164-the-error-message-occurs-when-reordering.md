---
title: ACSD-65164：在選取了單一核取方塊自訂選項的情況下重新排序可設定產品時出現錯誤訊息
description: 套用ACSD-65164修補程式來修正Adobe Commerce問題，其中錯誤訊息*某些選取的專案選專案前無法使用*當使用單一選取的核取方塊自訂選項重新排序可設定產品時發生。
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164：在選取了單一核取方塊自訂選項的情況下重新排序可設定產品時出現錯誤訊息

ACSD-65164修補程式修正錯誤訊息&#x200B;*某些選取的專案選專案前無法使用*&#x200B;的問題，當使用單一選取的核取方塊自訂選項重新排序可設定的產品時。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 修補程式ID為ACSD-65164。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用單一選取的核取方塊自訂選項重新排序可設定產品時，系統傳回錯誤訊息： *某些選取的專案選專案前無法使用*。

### 復寫步驟：

1. 在管理面板中，移至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**。
1. 在&#x200B;**[!UICONTROL Customizable Options]**&#x200B;底下，新增&#x200B;*核取方塊*&#x200B;選項。
   * 將核取方塊選項設為&#x200B;*必要*。
   * 新增兩個選項值。
1. 瀏覽至店面，並以註冊客戶身分登入。
1. 在選取一個核取方塊選項的情況下將產品新增到購物車。
1. 前往&#x200B;**[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**。
1. 移至「**[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]**」以新增相同的產品。

**預期結果：**

產品應該已成功新增到購物車。

**實際結果：**

系統會顯示錯誤訊息：

*無法將SKU為「24-MB01」的產品新增至購物車：某些選取的專案選專案前無法使用。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
