---
title: ACSD-64212：下訂單後，訂單未連結至透過 [!DNL GraphQL] 建立的客戶帳戶
description: 套用ACSD-64212修補程式以修正Adobe Commerce訂單無法連結至客戶帳戶（於下訂單後透過 [!DNL GraphQL] 建立）的問題。
feature: GraphQL, Checkout, Customers
role: Admin, Developer
exl-id: be62e635-2a61-41ed-9c1d-b2c54ee01024
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212：下訂單後，訂單未連結至透過[!DNL GraphQL]建立的客戶帳戶

ACSD-64212修補程式修正了下訂單後，訂單無法連結至透過[!DNL GraphQL]建立的客戶帳戶的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-64212。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在下單後透過[!DNL GraphQL]建立帳戶時，訂單未連結到客戶帳戶。

<u>要再現的步驟</u>：

1. 在前端下賓客訂單。
1. 傳送以下要求以建立帳戶：

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>預期結果</u>：

建立客戶帳戶後，來賓訂單會與客戶相關聯。

<u>實際結果</u>：

已建立客戶帳戶，但來賓訂單未與客戶相關聯。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
