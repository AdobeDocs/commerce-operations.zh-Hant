---
title: ACSD-65750： [!DNL GraphQL] "route"查詢傳回在 [!DNL Page Builder] 產品內容型別中順序不正確的產品
description: 套用ACSD-65750修補程式以修正GraphQL「route」查詢在 [!DNL Page Builder] Products內容型別中傳回產品不符順序的Adobe Commerce問題。
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750： [!DNL GraphQL]「route」查詢傳回在[!DNL Page Builder]產品內容型別中順序不正確的產品

ACSD-65750修補程式修正了[!DNL GraphQL]「route」查詢傳回[!DNL Page Builder]產品內容型別中順序不正確的產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-65750。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用[!DNL GraphQL]產品內容型別時，[!DNL Page Builder]「路由」查詢未傳回正確排序順序的產品。

<u>要再現的步驟</u>：

1. 在目錄中建立新類別和部分產品，並將產品連結至此類別。
1. 導覽至「**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**」，編輯建立的類別，並開啟「**[!UICONTROL Products in Category]**」標籤。
1. 為此類別中的每個產品設定自訂&#x200B;**[!UICONTROL Position]**。
1. 儲存類別並執行重新索引。
1. 導覽至「**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**」，然後按一下「**[!UICONTROL Add New Page]**」。
1. 展開&#x200B;**[!UICONTROL Content]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Edit with Page Builder]**。
1. 將&#x200B;**[!UICONTROL Row]**&#x200B;元素拖曳至內容區域，然後將&#x200B;**[!UICONTROL Products]**&#x200B;元素拖曳至列內。
1. 依照以下方式設定Products元素：
   * **[!UICONTROL Select Products By]**： *類別*
   * **[!UICONTROL Category]**： *選取新建立的類別*
   * **[!UICONTROL Sort By]**： *位置*
1. 切換至&#x200B;**[!UICONTROL Search Engine Optimization]**&#x200B;標籤，並將&#x200B;**[!UICONTROL URL Key]**&#x200B;設定為&#x200B;*test-widget*。
1. 儲存頁面。
1. 提出下列[!DNL GraphQL]要求：

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>預期結果</u>：

系統會依照產品類別位置所定義的順序傳回產品。

<u>實際結果</u>：

系統會以不符合GraphQL回應中類別位置的順序傳回產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
