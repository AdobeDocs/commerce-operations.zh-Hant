---
title: ACSD-53204： *無法儲存產品*將影像新增至相簿的同時請求發生錯誤
description: 套用ACSD-53204修補程式以修正Adobe Commerce問題，其中使用rest/V1/products/&amp；lt；sku&amp；gt；/media端點同時請求將影像新增至產品相簿時會擲回無法儲存產品錯誤。
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204：將影像新增至相簿的並行請求中出現「*無法儲存產品*」錯誤

ACSD-53204修補程式修正了使用`rest/V1/products/<sku>/media`端點同時請求將影像新增至產品相簿時擲回「*無法儲存產品*」錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-53204。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用`rest/V1/products/<sku>/media`端點同時要求將影像新增至產品相簿時，擲回&#x200B;*無法儲存產品*&#x200B;錯誤。

<u>要再現的步驟</u>：

1. 登入「管理面板」。
1. 使用SKU p1建立產品。
1. 對`rest/V1/products/<sku>/media`端點同時提出多個要求，以同時上傳多個影像。

<u>預期結果</u>：

影像儲存時不會發生錯誤。

<u>實際結果</u>：

「*無法儲存產品*」錯誤不時傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
