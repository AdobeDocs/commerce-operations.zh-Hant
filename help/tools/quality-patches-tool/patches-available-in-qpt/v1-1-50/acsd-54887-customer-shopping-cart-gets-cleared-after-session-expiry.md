---
title: ACSD-54887：客戶購物車在客戶工作階段過期後清除
description: 套用ACSD-54887修補程式以修正Adobe Commerce問題，該問題導致客戶購物車在啟用[!UICONTROL Persistent Shopping Cart]的客戶工作階段過期後獲得清除。
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887：客戶購物車在客戶工作階段過期後清除

ACSD-54887修補程式修正了客戶工作階段過期（啟用[!UICONTROL Persistent Shopping Cart]）後客戶購物車被清除的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-54887。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p8、2.4.5-p3 - 2.4.5-p7和2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶購物車在客戶工作階段過期之後清除，並啟用[!UICONTROL Persistent Shopping Cart]。

<u>要再現的步驟</u>：

1. 啟用[!UICONTROL Persistent Shopping Cart]。 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *是*。

   在啟用「持續性」的情況下登入（注意：它不適用於快顯授權，但僅適用於直接[!UICONTROL Sign in]頁面）。

1. 新增產品至購物車。
1. 繼續結帳，並選取付款方式。
1. 使工作階段過期（刪除`PHPSESSID`）。
1. 重新整理頁面。 請注意，報價會立即轉換為來賓報價，因為已選取付款方式，且已移除[!UICONTROL Persistent Cart] Cookie。
1. 使工作階段過期（刪除`PHPSESSID`）。
1. 重新整理頁面。 檢視購物車是空的。
1. 再次登入。

<u>預期結果</u>：

當您再次登入時，購物車有產品。

<u>實際結果</u>：

再次登入時，購物車是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
