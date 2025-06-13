---
title: ACSD-56447：透過平行網頁REST API將相同產品新增到購物車中會產生兩個不同的專案
description: 套用ACSD-56447修補程式以修正Adobe Commerce問題，其中透過平行網頁REST API請求將相同產品新增到購物車會在購物車中產生兩個單獨的專案。
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447：透過平行網頁REST API將相同產品新增到購物車中會產生兩個不同的專案

ACSD-56447修補程式修正透過平行網頁REST API請求將相同產品新增到購物車會在購物車中產生兩個單獨專案的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-56447。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過平行網頁REST API請求將相同的產品新增到購物車中，會在購物車中產生兩個不同的專案。

<u>要再現的步驟</u>：

1. 產生客戶Token，以使用[!DNL Postman]發出REST API呼叫請求。
1. 為客戶建立購物車。
1. 使用上面產生的Token來建立客戶的空購物車。
1. 使用CURL讓兩個`AddProductsToCart`請求並行執行。 按照開發人員檔案中的[訂單處理教學課程](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/)中的指示進行。

<u>預期結果</u>：

具有多個數量的料號會顯示在一行中。

<u>實際結果</u>：

相同的SKU會顯示在多個條列專案中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
