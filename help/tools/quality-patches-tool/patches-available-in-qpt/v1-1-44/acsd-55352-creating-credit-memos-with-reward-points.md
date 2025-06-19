---
title: ACSD-55352：以獎勵點數建立銷退折讓單
description: 套用ACSD-55352修補程式以修正Adobe Commerce問題，其中在建立包含客戶獎勵點數的部分銷退折讓單後，訂單狀態會變更為*closed*，而銷退折讓單選項會從管理訂單頁面消失。
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352：以獎勵點數建立銷退折讓單

ACSD-55352修補程式修正下列問題：使用客戶獎勵點數建立部分銷退折讓單後，訂單狀態變更為&#x200B;*已關閉*，且銷退折讓單選項從管理訂單頁面消失。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-55352。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用客戶獎勵點數建立部分銷退折讓單後，訂單狀態會變更為&#x200B;*已關閉*，而銷退折讓單選項會從管理訂單頁面消失。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員。
2. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**」。
3. 新增兩個費率：
   * *[!UICONTROL First]*：
      * *[!UICONTROL Direction]* = *指向貨幣*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*：
      * *[!UICONTROL Direction]* = *貨幣到點*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. 建立簡單的產品，其價格為&#x200B;*$100*&#x200B;且&#x200B;*數量*： *100*。
5. 從店面建立客戶。
6. 再次前往後端： **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** >新增&#x200B;*100*&#x200B;並儲存客戶。
7. 前往店面，並以客戶先前建立的身分登入。
8. 將產品加入購物車，數量為&#x200B;*Qty*： *10*。
9. 移至&#x200B;**[!UICONTROL Checkout]**&#x200B;並在提示時使用可用的&#x200B;*100*&#x200B;獎勵點數並下訂單。
10. 移至「**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]**」並送出該訂單。
11. 移至[!UICONTROL Credit Memo]並將&#x200B;*退款數量*&#x200B;更新為&#x200B;*8*。
12. 勾選&#x200B;**[!UICONTROL Refund Reward Points]**&#x200B;核取方塊，然後按一下&#x200B;**[!UICONTROL Refund offline]**。
13. 嘗試使用[!UICONTROL Credit Memo]退款訂單中其餘的兩個產品。

<u>預期結果</u>：

* 管理員建立[!UICONTROL Credit Memo]以傳回其餘兩個產品。
* 訂單狀態為&#x200B;*已完成*。

<u>實際結果</u>：

* 無法建立更多[!UICONTROL Credit Memo]。
* 訂單狀態為&#x200B;*已關閉*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
