---
title: ACSD-56790：排序 [!DNL Visual Merchandiser]中的產品時，**[!UICONTROL move out of stock to bottom]**選項無法運作
description: 套用ACSD-56790修補程式，修正Adobe Commerce在視覺化商品銷售中排序產品時，從庫存移至底部選項無法運作的問題。
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790：在[!DNL Visual Merchandiser]中排序產品時，**[!UICONTROL move out of stock to bottom]**&#x200B;選項無法運作

ACSD-56790修補程式修正在[!DNL Visual Merchandiser]中排序產品時，從庫存移至底部選項無法運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-56790。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排序[!DNL Visual Merchandiser]中的產品時，**[!UICONTROL move out of stock to bottom]**&#x200B;選項無法運作

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**」並建立下列屬性。
1. 建立新網站： **非主要**。
1. 在這個新網站上建立&#x200B;**非主要商店**。
1. 建立兩個存放區：

   * 在&#x200B;**主要網站商店**&#x200B;中排在首位。
   * 在&#x200B;**非主要存放區**&#x200B;中的第二個。

1. 建立兩個來源：
   * 字母。
   * 數字。

1. 建立兩個庫存：
   * 第一個主要 — 銷售管道：主要網站 — 指派的來源：信件。
   * 第二個非主要 — 銷售管道：非主要 — 指定來源：數字。

1. 在兩個網站上建立三個簡單的產品，全部在預設類別中，全部指派給兩個來源：

   * ProductA — 數量&#x200B;*10*&#x200B;為字母，數量&#x200B;*0*&#x200B;為數字。
   * Product1 — 數量&#x200B;*0*&#x200B;為字母，數量&#x200B;*10*&#x200B;為數字。
   * ProductA1 — 數量&#x200B;*10*&#x200B;為字母，數量&#x200B;*10*&#x200B;為數字。

1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;並選取&#x200B;**[!UICONTROL Default category]**。
1. 將範圍變更為&#x200B;**第一個**。
1. 展開「類別」區段中的「產品」 。
1. 挑選排序順序為： **[!UICONTROL move out of stock to bottom]**

<u>預期結果</u>：

具有&#x200B;**無庫存**&#x200B;產品的產品清單移至底部。

<u>實際結果</u>：

產品無法載入。 頁面會重新導向至管理儀表板，並顯示錯誤訊息： `Invalid security or form key. Please refresh the page`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
