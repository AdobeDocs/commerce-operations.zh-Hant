---
title: ACSD-46988：GraphQL貨幣API要求傳回null值
description: ACSD-46988修補程式修正GraphQL貨幣API請求傳回自訂貨幣的null值的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21後，即可使用此修補程式。 修補程式ID為ACSD-46988。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988：GraphQL貨幣API要求傳回null值

ACSD-46988修補程式修正GraphQL貨幣API請求傳回自訂貨幣的null值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46988。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL currency API要求傳回自訂貨幣的null值。

<u>要再現的步驟</u>：

1. 在「管理員」中設定自訂貨幣。 移至&#x200B;**系統** > **組態** > **一般** > **貨幣設定**。
1. 傳送包含下列裝載的GraphQL請求：

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>預期結果</u>：

該請求會傳回貨幣值而不是null值。

<u>實際結果</u>：

該請求會傳回多個null值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [品質修補工具>使用狀況](/help/tools/quality-patches-tool/usage.md) （在品質修補工具指南中）。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 安裝修補程式後所需的其他步驟

對於內部部署使用者：

* 執行： `composer require symfony/intl:"~5.4.11"`

對於雲端使用者：

* 執行： `composer require symfony/intl:"~5.4.11"`
* 將`composer.json`和`composer.lock`檔案連同修補程式檔案一起推送到Git存放庫。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱「品質修補程式工具」指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
