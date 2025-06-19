---
title: MDVA-39195：「類別」頁面上的「加入購物車」為非作用中
description: MDVA-39195修補程式解決啟用重新導向至購物車時，「類別」頁面上的**加入購物車**按鈕失效的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39195。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: Categories, Orders, Shopping Cart
role: Admin
exl-id: 2c391f54-3b9e-4e72-944b-b003e4ade9b9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-39195：「類別」頁面上的「加入購物車」為非作用中

MDVA-39195修補程式可解決啟用重新導向至購物車時，**加入購物車**&#x200B;按鈕在類別頁面上的非使用中問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39195。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用重新導向至購物車時，**加入購物車**&#x200B;按鈕在類別頁面上處於非使用中狀態。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** >設定> **組態** > **銷售** > **結帳**。
1. 展開&#x200B;**購物車**&#x200B;區段。
1. 新增產品重新導向至購物車&#x200B;**後，將**&#x200B;設定為「是」。
1. 造訪類別頁面。

<u>預期結果</u>：

**加入購物車**&#x200B;在類別頁面上作用中。

<u>實際結果</u>：

**加入購物車**&#x200B;按鈕在類別頁面上為非作用中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
