---
title: 'ACSD-66434：公司[!UICONTROL Customer ID]查詢中缺少 [!DNL GraphQL] '
description: 套用ACSD-66434修補程式以修正公司[!UICONTROL Customer ID]查詢中缺少 [!DNL GraphQL] 的Adobe Commerce問題。
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: e60194341bf79ca3ecdc505cf30f226b8f1b6c7f
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-66434：公司[!UICONTROL Customer ID]查詢中缺少[!DNL GraphQL]

ACSD-66434修補程式修正公司&#x200B;**[!UICONTROL Customer ID]**&#x200B;查詢中缺少[!DNL GraphQL]的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66434。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p10 - 2.4.6-p11， 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL GraphQL]公司查詢傳回公司結構中`null`的&#x200B;**[!UICONTROL Customer ID]**。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce 2.4 — 使用B2B和詳細目錄模組開發。
1. 從「Commerce管理員」啟用B2B功能並建立測試公司。
1. 使用下列[!DNL GraphQL]變更為公司管理員產生持有人權杖：

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 使用產生的Token透過下列[!DNL GraphQL]查詢擷取客戶的公司結構：

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>預期結果</u>：

公司&#x200B;**[!UICONTROL Customer ID]**&#x200B;查詢中應傳回[!DNL GraphQL]。

<u>實際結果</u>：

**[!UICONTROL Customer ID]**&#x200B;在公司`null`查詢中傳回為[!DNL GraphQL]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
