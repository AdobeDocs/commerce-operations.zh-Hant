---
title: MDVA-41631：擷取不含可選「電話」值的訂單資訊時發生錯誤
description: MDVA-41631修補程式修正使用者擷取訂單資訊時，若未透過選用的電話值，則會發生錯誤的問題。  [!DNL GraphQL]安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631：擷取不含可選「電話」值的訂單資訊時發生錯誤

MDVA-41631修補程式修正使用者透過[!DNL GraphQL]擷取訂單資訊時，若無選擇性「電話」值，會發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者透過[!DNL GraphQL]擷取訂單資訊時，若沒有選擇性的「電話」值，則會發生錯誤。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **客戶** > **客戶設定** > **名稱和地址選項** > **顯示電話**&#x200B;並將電話號碼設定為選用。
1. 使用[!DNL GraphQL API]作為登入客戶下訂單。
   * 設定帳單和運送地址時不要設定電話號碼。 按照開發人員檔案中的[[!DNL GraphQL] 結帳教學課程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)中的指示進行。
1. 使用[!DNL GraphQL] [`customerOrders`查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/)擷取訂單。

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>預期結果</u>：

使用者取得訂單資訊。

<u>實際結果</u>：

使用者收到下列錯誤： *&quot;message&quot;： &quot;Internal server error&quot;，*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
