---
title: ACSD-56546：可設定和套裝產品在店面顯示為無庫存
description: 套用ACSD-56546修補程式來修正Adobe Commerce問題，此問題發生在停用*[!UICONTROL Display Out of Stock Products]*組態選項時，可設定和套件組合產品在店面顯示為無庫存。
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546：可設定和套裝產品在店面顯示為無庫存

ACSD-56546修補程式修正可設定和套裝產品在店面顯示為無存貨的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-56546。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

停用&#x200B;*[!UICONTROL Display Out of Stock Products]*&#x200B;選項時，可設定和套裝產品在店面顯示為無庫存。

<u>要再現的步驟</u>：

1. 將&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;選項設為&#x200B;*否*。
1. 建立網站、商店和商店評論。
1. 建立來源和庫存，然後將其指派給第二個網站。
1. 建立具有兩個子產品的&#x200B;*可設定產品*。 將兩個子產品同時指派給來源和兩個網站。
1. 更新第一個子產品，使兩個來源中的&#x200B;*qty=0*。
1. 更新第二個子產品，並在第二個網站上停用它。
1. 執行完整重新索引。
1. 檢查包含第二個網站上可設定產品的類別。

<u>預期結果</u>：

沒有庫存的可設定產品在店面中不可見。

<u>實際結果</u>：

即使停用&#x200B;*[!UICONTROL Display Out of Stock Products]*&#x200B;選項，沒有庫存的可設定產品也會顯示在店面上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
