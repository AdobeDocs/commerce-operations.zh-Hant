---
title: 「ACSD-61528：使用GraphQL擷取角色未傳回任何結果」
description: 套用ACSD-61528修補程式以解決Adobe Commerce問題，該問題導致使用GraphQL從公司管理員處擷取角色時一律傳回null結果。
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 4a02bb524fd8d1caae02d909bc9f2e3fc0112042
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528：使用GraphQL擷取角色未傳回任何結果

ACSD-61258修補程式修正使用GraphQL從公司管理員擷取角色時，一律會傳回null結果的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-61528。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用GraphQL從公司管理員擷取角色時，角色結果一律為空。

<u>必要條件：</u>：

安裝並啟用Adobe Commerce B2B模組。

<u>要再現的步驟</u>：

1. 建立公司。
1. 以公司管理員身分登入GraphQL，使用下列突變：

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. 將產生的Token新增至&#x200B;**Authorization**&#x200B;要求標頭做為`Bearer`Token，並在GraphQL查詢底下執行：

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>預期結果</u>：

GraphQL查詢會傳回角色。

<u>實際結果</u>：

公司的角色為null。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。