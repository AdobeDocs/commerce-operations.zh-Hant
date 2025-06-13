---
title: MDVA-40961：當購物車中已有最小數量的專案時，無法將其他專案新增到購物車中
description: MDVA-40961修補程式修正當購物車中已有最小專案數量時，無法將其他專案新增到購物車的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-40961。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Orders, Shopping Cart
role: Admin
exl-id: b5191919-062d-4ddd-84e2-a4801501724d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961：當購物車中已有最小數量的專案時，無法將其他專案新增到購物車中

MDVA-40961修補程式修正當購物車中已有最小專案數量時，無法將其他專案新增到購物車的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-40961。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當購物車中已有專案的最小數量時，無法將其他專案新增到購物車中。

<u>要再現的步驟</u>：

1. 將簡單產品設定為購物車&#x200B;**中允許超過一個**&#x200B;最小數量 （例如，兩個）。
1. 在店面開啟產品，並將其中兩個加入購物車。
1. 停留在產品頁面上，並將此產品的另一個產品新增到購物車。

<u>預期結果</u>：

第三個產品已包含最小量，可以新增到購物車中。

<u>實際結果</u>：

您收到下列錯誤訊息： *您可購買的次數最少為2*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
