---
title: ACSD-65254：透過updateCustomerEmail [!DNL GraphQL] 突變更新客戶電子郵件後未傳送電子郵件通知
description: 套用ACSD-65254修補程式，修正使用updateCustomerEmail [!DNL GraphQL] 突變成功更新客戶帳戶上的電子郵件地址後，未傳送電子郵件通知給客戶的Adobe Commerce問題。
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5f7af7704c53c808298422dc165397dd255480b9
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# ACSD-65254：透過`updateCustomerEmail` [!DNL GraphQL]突變更新客戶電子郵件後未傳送電子郵件通知

ACSD-65254修補程式修正使用`updateCustomerEmail` [!DNL GraphQL]突變更新客戶帳戶上的電子郵件地址後，未傳送電子郵件通知給客戶的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-65254。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用`updateCustomerEmail` [!DNL GraphQL]突變更新客戶的電子郵件地址後，未傳送電子郵件通知給客戶。

<u>要再現的步驟</u>：

1. 使用以下變異建立使用者：

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. 為先前建立的使用者產生代號，並作為持有人權杖使用：

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. 嘗試使用上次建立的持有人權杖更新先前建立之使用者的電子郵件：

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>預期結果</u>：

客戶更新其帳戶上的電子郵件地址後，應該會收到電子郵件通知。

<u>實際結果</u>：

只會將訂閱電子郵件傳送到新地址；不會傳送電子郵件地址變更的確認電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
