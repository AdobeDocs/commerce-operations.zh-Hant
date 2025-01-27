---
title: ACSD-61895： [!DNL GraphQL] 類別查詢無法以受限制的檢視查詢私用共用目錄
description: 套用ACSD-61895修補程式來修正Adobe Commerce問題，若為相同類別建立具有限制的私人共用類別目錄時，來賓客戶的 [!DNL GraphQL] 回應（使用具有所有允許類別的公開共用目錄）未傳回任何類別。
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895：具有受限制檢視的私人共用目錄的[!DNL GraphQL] `categories`查詢失敗

ACSD-61895修補程式修正為相同類別建立具有限制的私人共用目錄時，訪客客戶的[!DNL GraphQL]回應（使用具有所有允許類別的公開共用目錄）未傳回任何類別的問題。

修正後，系統傳回所有具有訪客使用者允許許可權（公開共用目錄）的類別，即使根類別在私人共用目錄範圍內沒有允許許可權。

安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-61895。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

為相同類別建立具有限制的私人共用目錄時，來賓客戶的[!DNL GraphQL]回應（使用具有所有允許類別的公開共用目錄）不會傳回任何類別。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce搭配B2B和範例資料。
1. 請確定B2B功能已啟用。
1. 建立兩個共用目錄：一個是公用目錄，一個是私用目錄。

   * 公用共用目錄：

      * 將所有類別指派給公用目錄。

   * 私人共用目錄：

      * 只將`Gear`類別及其子類別指派給私人目錄。
      * 將私人目錄指派給測試公司。

1. 建立公司使用者：

   * 建立與連結至私人共用目錄之測試公司相關聯的使用者。
   * 確保使用者登入時只能在前端存取`Gear`類別及其子類別。

1. 透過API查詢類別：

   * 使用API使用者端來執行下列[!DNL GraphQL]查詢，而不使用客戶權杖：

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. 觀察回應，並確認是否傳回`Gear`類別與其他類別。
1. 現在使用客戶Token查詢類別：

   * 以測試公司使用者的身分登入。
   * 執行相同的[!DNL GraphQL]類別查詢，但包含登入使用者的客戶權杖。
   * 觀察回應，並檢查是否只傳回`Gear`類別及其子類別。


<u>預期結果</u>：

以訪客公司使用者身分進行查詢時，所有類別都應傳回（如預期）。

<u>實際結果</u>：

來自`categories`查詢的回應未顯示任何類別。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。

