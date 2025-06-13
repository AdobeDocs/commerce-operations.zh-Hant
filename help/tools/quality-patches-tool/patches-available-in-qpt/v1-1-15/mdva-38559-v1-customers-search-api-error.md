---
title: MDVA-38559： /V1/customers/search API傳回錯誤
description: MDVA-38559修補程式修正'/V1/customers/search' API對擁有多個訂閱的客戶傳回錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-38559。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: REST, Search
role: Admin
exl-id: 6bcb65d0-1389-4090-b53c-8048bf64d8fb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-38559： /V1/customers/search API傳回錯誤

MDVA-38559修補程式修正`/V1/customers/search` API為具有多個訂閱的客戶傳回錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-38559。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`/V1/customers/search` API為具有多個訂閱的客戶傳回錯誤。

<u>必要條件</u>：

Adobe Commerce商店使用多個網站。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **客戶** > **客戶設定** > **帳戶共用選項**，然後選取&#x200B;**全域**。
1. 移至&#x200B;**客戶** > **所有客戶**，選取任何客戶的&#x200B;**編輯**，然後選取&#x200B;**電子報**。
1. 訂閱一個以上網站的電子報並儲存客戶。
1. 傳送下列請求：

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>預期結果</u>：

會顯示客戶的搜尋結果。

<u>實際結果</u>：

下列錯誤記錄至exception.log： *相同識別碼「1」的專案(Magento\Customer\Model\Customer\Interceptor)已經存在。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
