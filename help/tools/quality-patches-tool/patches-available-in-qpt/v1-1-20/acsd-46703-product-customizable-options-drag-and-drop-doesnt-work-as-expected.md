---
title: ACSD-46703：產品自訂拖放無法運作
description: 針對產品可自訂選項拖放功能無法正常運作的問題，本文提供解決方案。
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-46703：產品自訂拖放無法運作

ACSD-46703修補程式修正了產品可自訂選項（拖放）無法如預期運作的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-46703。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他具有新[品質修補程式工具]發行版本的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法將可自訂選項從一個頁面拖放至另一個頁面。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 將可自訂的選項新增至簡單產品，並確定新增20個以上的選項會造成分頁。
1. 嘗試在同一頁面中移動可自訂的選項（拖放）。
1. 現在嘗試將可自訂選項從第二頁移至第一頁。

<u>預期結果</u>：

* 您可將可自訂選項從一個頁面拖放至另一個頁面。
* 即使對於多個頁面，您仍可使用拖放功能來排序值。

<u>實際結果</u>：

您無法使用拖放功能將任何值移至其他頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [品質修補工具>使用狀況](/help/tools/quality-patches-tool/usage.md) （在品質修補工具指南中）。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
