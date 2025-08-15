---
title: ACSD-62332：產品清單GraphQL查詢限製為10,000個產品，且 [!DNL Live Search] 將目前頁面設為1
description: 套用ACSD-62332修補程式以修正Adobe Commerce問題，其中產品清單GraphQL查詢限製為total_count 10,000個產品，且在透過GraphQL查詢時，在搜尋條件中 [!DNL Live Search] 將目前頁面設定為*1*而不是頁面*2*。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332：產品清單GraphQL查詢限製為10,000個產品，且[!DNL Live Search]將目前頁面設為1

>[!NOTE]
>
>此修補程式是[ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md)的更新版本，並在2.4.6 - 2.4.6-p8版本上取代[ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md)。 如需更多詳細資訊，請參閱相應的文章。

ACSD-62332修補程式修正了產品清單GraphQL查詢限製為10,000項產品中的`total_count`的問題，以及[!DNL Live Search]透過GraphQL查詢時，在搜尋條件中將目前頁面設定為&#x200B;*1*&#x200B;而非頁面&#x200B;*2*&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-62332。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品清單GraphQL查詢限製為total_count 10,000個產品，其中[!DNL Live Search]透過GraphQL查詢時，在搜尋條件中將目前頁面設定為&#x200B;*1*&#x200B;而非頁面&#x200B;*2*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
