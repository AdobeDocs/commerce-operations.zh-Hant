---
title: ACSD-51683：無法使用GraphQL將可自訂選項新增到購物車
description: 套用ACSD-51683修補程式，修正無法使用GraphQL將可自訂選項新增到購物車的Adobe Commerce問題。
feature: GraphQL
role: Admin
exl-id: 9cdf71aa-3dea-4f8c-b4d6-d6f192a9710d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51683：無法使用GraphQL將可自訂選項新增到購物車

ACSD-51683修補程式修正無法使用GraphQL將可自訂選項新增到購物車的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51683。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

可自訂選項無法使用GraphQL新增到購物車。

<u>要再現的步驟</u>：

1. 使用可自訂的&#x200B;**文字欄位**&#x200B;選項建立簡單產品。
1. [透過GraphQL將具備必要可自訂選項的已建立產品加入購物車](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/)。
1. 傳送[購物車](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL要求以檢查購物車中的產品及其詳細資料。

<u>預期結果</u>

GraphQL回應中的`Customizable_options`區段包含將產品新增至購物車時提供的資料。

<u>實際結果</u>

GraphQL回應中的`Customizable_options`區段是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
