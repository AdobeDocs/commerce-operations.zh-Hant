---
title: ACSD-54418：固定折扣金額錯誤地新增到動態定價套件的子產品中
description: 套用ACSD-54418修補程式，修正動態定價套裝的每個子產品不正確套用固定折扣金額的Adobe Commerce問題。
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418：動態定價套裝的子產品不正確地新增了固定折扣金額。

ACSD-54418修補程式修正動態定價套件組合的每個子產品不正確套用固定折扣金額的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-54418。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

固定折扣金額錯誤地套用至動態定價套件的每個子產品。

<u>要再現的步驟</u>：

1. 使用動態定價和&#x200B;*2*&#x200B;套件組合選項建立&#x200B;**[!UICONTROL bundle product]**。
1. 使用只適用於捆綁產品&#x200B;**[!UICONTROL SKU]**&#x200B;且具有固定折扣的特定優惠券代碼來建立&#x200B;**[!UICONTROL cart price rule]**。
1. 將隨附產品新增到購物車。
1. 套用&#x200B;**[!UICONTROL coupon code]**。
1. 檢查套用至購物車的折扣。

<u>預期結果</u>：

此折扣只會套用至整個套裝產品一次。

<u>實際結果</u>：

折扣會套用至每個套件組合子產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
