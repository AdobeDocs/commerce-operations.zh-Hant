---
title: ACSD-61553：套用不同優先順序的多個折扣時，[!UICONTROL Cart Price Rule]計算不正確
description: 套用ACSD-61553修補程式以解決套用具有不同優先順序的多個折扣時，未正確計算[!UICONTROL Cart Price Rule]的Adobe Commerce問題。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553：套用不同優先順序的多個折扣時，[!UICONTROL Cart Price Rule]計算不正確

ACSD-61553修補程式修正了套用不同優先順序的多個折扣時，[!UICONTROL Cart Price Rule]計算錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-61553。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p8

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用具有不同優先順序的多個折扣時，[!UICONTROL Cart Price Rule]計算不正確。

<u>要再現的步驟</u>：

1. 建立價格$9,000的簡單產品。
1. 建立[!UICONTROL Cart Price Rule]：規則A，固定折扣為$700，不附帶任何條件且不捨棄後續規則。
1. 建立另一個[!UICONTROL Cart Price Rule]：規則B，固定折扣為$1000，沒有任何條件，且不放棄後續規則。
1. 將數量為13的產品新增至購物車。
1. 使用下列任一案例更新規則：

   案例01

       規則A
       優先順序： 1
       最大數量折扣套用至： 1
       
       規則B
       優先順序： 0
       最大數量折扣套用至： 0
   
   案例02

       規則A
       優先順序： 0
       最大數量折扣套用至： 0
       
       規則B
       優先順序： 1
       最大數量折扣套用至： 1
   
   案例03

       規則A
       優先順序： 0
       最大數量折扣套用至： 0
       
       規則B
       優先順序： 0
       最大數量折扣套用至： 1
   
1. 按一下&#x200B;**[!UICONTROL Update Shopping Cart]**&#x200B;按鈕以重新計算折扣。

<u>預期結果</u>：

您會看到不同案例的下列總折扣：

    案例01：$13,700
    案例02：$10,100
    案例03：$10,100

<u>實際結果</u>：

在這三種情況中，總折扣為$9,000。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
