---
title: '''MDVA-41631：擷取不含選擇性「電話」值的訂單資訊時發生錯誤'
description: MDVA-41631修補程式修正使用者透過GraphQL擷取訂單資訊（不含選擇性「電話」值）時發生錯誤。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Orders
role: Admin
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-41631：擷取不含可選「電話」值的訂單資訊時發生錯誤

MDVA-41631修補程式修正使用者透過GraphQL擷取訂單資訊（不含選擇性「電話」值）時發生錯誤。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，此問題計劃在 Adobe Systems Commerce 2.4.4 中修正。

## 受影響的產品和版本

**此修補程式是為商務版本Adobe Systems建立的：**

Adobe Systems Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若未使用選用的「電話」值，使用者透過GraphQL擷取訂單資訊時發生錯誤。

<u>重現</u>步驟：

1. 轉到&#x200B;**>**&#x200B;配置&#x200B;**>** **客戶**&#x200B;存儲>**客戶配置**>**姓名和地址選項**>**顯示電話**“，並將電話號碼設置為可選。
1. 使用 GraphQL API 作為登錄客戶下訂單。
   * 設定帳單和送貨地址時，請勿設定電話號碼。 按照我們開發人員文檔中的 GraphQL 結帳教程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-customer.html)中[給出的說明進行操作。
1. 使用GraphQL [customerOrders查詢](https://developer.adobe.com/commerce/webapi/graphql/queries/customer-orders.html)擷取訂單。

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>預期結果</u>：

使用者取得訂單資訊。

<u>實際結果</u>：

使用者收到下列錯誤： *&quot;message&quot;： &quot;Internal server error&quot;，*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Systems Commerce on 雲端基礎結構： [> Commerce on Cloud 基礎架構指南中的升級和修補程式套用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 修補程式。

## 相關閱讀

要瞭解有關品質補丁工具的更多資訊，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
