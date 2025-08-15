---
title: ACSD-47027：緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新
description: 套用ACSD-47027修補程式以修正查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新速度緩慢的Adobe Commerce問題。
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027：緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新

ACSD-47027修補程式解決緩慢查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新無法如預期運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23時，即可使用此修補程式。 修補程式ID為ACSD-47027。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

慢速查詢B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新未如預期運作。

<u>必要條件</u>：

安裝B2B模組。

<u>要再現的步驟</u>：

1. 在Adobe Commerce Admin中，移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**&#x200B;並將&#x200B;**[!UICONTROL Enable Company]**&#x200B;設為&#x200B;_是_。
1. 前往前端並建立公司。
1. 以公司使用者身分登入後，請前往&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**&#x200B;並新增角色。
1. 使用[!UICONTROL dev]啟用`bin/magento dev:que:enab`查詢記錄。
1. 現在傳送以下[!DNL GraphQL]個請求（ID為[!UICONTROL base64]編碼角色ID）：

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. 檢查查詢記錄。
1. 您可以看到上述查詢已執行。 此查詢會在`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`中執行。

<u>預期結果</u>：

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`需要最佳化，以避免載入&#x200B;**[!UICONTROL company_permissions]** DB資料表中所有可用的資料。

<u>實際結果</u>：

Adobe Commerce會執行查詢，而不使用任何篩選器。 當有大量記錄時，Adobe Commerce會花很長時間準備資料收集。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
