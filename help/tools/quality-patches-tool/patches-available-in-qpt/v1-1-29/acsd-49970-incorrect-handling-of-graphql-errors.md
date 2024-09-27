---
title: 「ACSD-49970：GraphQL錯誤的處理不正確」
description: 套用ACSD-49970修補程式以修正[!UICONTROL New Relic Reporting]開啟時Adobe CommerceGraphQL錯誤處理方式不正確的問題。
feature: GraphQL, Observability
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970：GraphQL錯誤的處理不正確

ACSD-49970修補程式修正了&#x200B;*[!UICONTROL New Relic Reporting]*&#x200B;開啟時無法正確處理GraphQL錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49970。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無論`logDataHelper`是否包含這個金鑰，`GraphQLOperationNames`金鑰處理不正確。

<u>要再現的步驟</u>：

1. 執行`bin/magento deploy:mode:set developer`。
1. 登入管理員。
1. 從&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**&#x200B;啟用&#x200B;**[!UICONTROL New Relic Integration]**
（注意：即使顯示錯誤指出[!DNL New Relic]擴充功能無法使用，也會儲存設定）。
1. 從&#x200B;*[!DNL Altair]*&#x200B;使用者端或任何其他使用者端或透過cURL執行此&#x200B;*GraphQL*&#x200B;突變至`http://yourMagentoDomain/graphql`。

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   （注意：請先將&#x200B;**[!UICONTROL Header]**&#x200B;設為[!UICONTROL Content-Currency:CA]，再執行）。

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>預期結果</u>：

記錄中沒有&#x200B;*500例外狀況*，正在正確處理`GraphQLOperationNames`金鑰。

<u>實際結果</u>：

記錄中發生&#x200B;*500例外狀況*，`GraphQLOperationNames`金鑰未正確處理。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
