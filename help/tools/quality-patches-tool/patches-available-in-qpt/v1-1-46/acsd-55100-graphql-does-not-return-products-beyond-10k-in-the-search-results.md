---
title: ACSD-55100： [!DNL GraphQL] 不會在搜尋結果中傳回超過10k的產品
description: 套用ACSD-55100修補程式，修正GraphQL未在搜尋結果中傳回超過*10k*之產品的Adobe Commerce問題。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-55100： [!DNL GraphQL]不會在搜尋結果中傳回超過10k的產品

ACSD-55100修補程式修正搜尋結果中[!DNL GraphQL]未傳回超過&#x200B;*10k*&#x200B;的產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46時，即可使用此修補程式。 修補程式ID為ACSD-55100。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL GraphQL]不會在搜尋結果中傳回超過&#x200B;*10k*&#x200B;的產品。

<u>必要條件</u>：

如果是&#x200B;**[!DNL OpenSearch]**，請確定您使用的是最新可用版本。

為了解決回報的問題，已引進時間點功能，此功能可在&#x200B;**[!DNL OpenSearch]** 2.5.0之後使用，且需要`opensearch-project/opensearch-php`封裝的2.2版本。

但是，與`magento/magento-cloud-metapackage`發生衝突，後者指定了`opensearch-project/opensearch-php`封裝上的相依性，該封裝應小於2.0.1版。


此相依性會防止將[opensearch-project/opensearch-php]套件更新至最新版本2.2。

因此，系統發生下列錯誤，並傳回超過&#x200B;*10,000*&#x200B;的產品的null結果。

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

現有的相依性使得直接將版本新增到`composer.json`檔案並將`opensearch-project/opensearch-php`封裝更新到版本2.2非常困難。

若要解決此問題，請在需要區塊下的主要`composer.json`檔案中加入下列行。 之後，請重新部署，以將有問題的套件更新至最新版本。

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>要再現的步驟</u>：

1. 產生包含&#x200B;*15k*&#x200B;產品的目錄。
1. 傳送[!DNL GraphQL]：

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>預期結果</u>：

總計_計數= *15k*
您應該能夠顯示所有產品。

<u>實際結果</u>：

總計_計數= *10k*
在*10k*&#x200B;批次之後，您無法再顯示任何產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
