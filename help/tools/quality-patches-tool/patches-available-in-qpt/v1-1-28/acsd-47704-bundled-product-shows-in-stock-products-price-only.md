---
title: ACSD-47704：套件產品僅顯示庫存產品的價格
description: 套用ACSD-47704修補程式來修正Adobe Commerce問題，若套件產品僅顯示庫存產品的價格。
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704：套件產品僅顯示庫存產品的價格

ACSD-47704修補程式修正客戶群組之間不正確快取客戶區段價格的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-47704。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已啟用動態定價的套件式產品價格不正確，因為僅包含庫存專案。

<u>要再現的步驟</u>：

1. 前往Commerce管理面板。
1. 前往「**[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**」。
1. 將&#x200B;**[UICONROL動態價格]**&#x200B;設定為&#x200B;**[!UICONTROL Yes]**。
1. 組合專案：
   * 將&#x200B;**[!UICONTROL Ship bundle items]**&#x200B;設為&#x200B;**[!UICONTROL Together]**
   * 選取&#x200B;**[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 標示必要的核取方塊
      * 新增任何有庫存的簡單產品；例如Joust Duffle Bag SKU 24-MB01。 新增產品之前，請記下價格 — $34
   * 預設數量：1
   * 選取&#x200B;**[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 標示必要的核取方塊
      * 新增任何有庫存的簡單產品，這些產品與之前步驟新增的產品不同；例如：Workfall Shall Pack 24-MB04。 新增產品之前，請記下價格 — $32
      * 預設數量：1
1. 儲存產品。
1. 前往店面，尋找在先前步驟中建立的產品。 記下價格 — $66
(66 = 32 + 34)。
目前，套裝產品的價格等於其選項的價格總和。
1. 前往Commerce管理面板。 前往&#x200B;**[!UICONTROL CATALOG]** > **[!UICONTROL Products]**。
1. 尋找其中一個先前指派為套件產品選項的簡單產品：
SKU 24-MB01，價格$34。
1. 將其數量變更為0。
1. 儲存產品。
1. 前往店面，尋找在先前步驟中建立的搭售產品。 記下價格 — $32。 之前定價為$66，SKU 24-MB01為$34，SKU 24-MB04為$32。 現在24-MB01產品已無庫存，則捆綁價格為$32美元。 這是其他產品的價格，亦即有庫存的選項。

<u>預期結果</u>：

無論選項是否有庫存或無庫存，啟用「動態定價」的套件組合產品價格計算方式均一致。

<u>實際結果</u>：

已啟用動態定價的套件組合產品價格計算錯誤。 它只會考慮有庫存的選項，這樣當其中一個選項無庫存時，顯示的金額會低於實際金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
