---
title: ACSD-62979： GraphQL標頭中的存放區ID不正確會導致嚴重的記憶體錯誤
description: 套用ACSD-62979修補程式來修正Adobe Commerce問題，該問題導致在GraphQL標頭中使用不正確的存放區ID發生嚴重的記憶體錯誤
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
source-git-commit: 187a0056971e6bec324b5cc9d374375bbfb84dd8
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979： GraphQL標頭中的存放區ID不正確會導致嚴重的記憶體錯誤

ACSD-62979修補程式修正在GraphQL標頭中使用不正確的存放區ID會導致嚴重記憶體錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62979。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6、2.4.6-p7、2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正在GraphQL標頭中使用不正確的存放區ID時，會導致嚴重記憶體錯誤的問題。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**。 啟用&#x200B;**[!UICONTROL Add Store Code to Urls]**。
1. 使用不正確的存放區標頭值在GraphQL查詢下方執行。

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>預期結果</u>：

錯誤訊息：「找不到要求的存放區。 請驗證商店，然後再試一次」

<u>實際結果</u>：

嚴重錯誤，例如：

```Allowed memory size of 792723456 bytes exhausted```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
