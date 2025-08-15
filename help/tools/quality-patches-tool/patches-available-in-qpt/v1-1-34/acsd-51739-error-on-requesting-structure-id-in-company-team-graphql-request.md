---
title: ACSD-51739：在「CompanyTeam」GraphQL請求中請求「structure_id」時發生錯誤
description: 套用ACSD-51739修補程式以修正Adobe Commerce問題，亦即在「CompanyTeam」GraphQL請求中要求「structure_id」時傳回錯誤。
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739：在`structure_id` GraphQL要求中要求`CompanyTeam`時發生錯誤

ACSD-51739修補程式修正在`structure_id` GraphQL請求中請求`CompanyTeam`時傳回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-51739。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在`structure_id` GraphQL要求中要求`CompanyTeam`時傳回錯誤。

<u>要再現的步驟</u>

1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**，並將&#x200B;*[!UICONTROL Enable Company]*&#x200B;設定為&#x200B;*是*。
1. 建立公司以及公司管理員使用者。
1. 建立新客戶(*customer1*)，並將公司（以上建立的）指派給此客戶。
1. 在前，以公司管理員使用者身分登入。
1. 建立公司團隊，並使用拖放將&#x200B;*customer1*&#x200B;指派給團隊。
1. 執行以下公司GraphQl查詢，包括具有`CompanyTeam`的`structure_id`：

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. 檢查GraphQL回應。

<u>預期結果</u>：

系統不會傳回任何錯誤，且GraphQL回應中會顯示所有要求的資料。

<u>實際結果</u>：

* 回應包含&#x200B;*內部伺服器錯誤*。
* `var/log/exception.log`包含：

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
