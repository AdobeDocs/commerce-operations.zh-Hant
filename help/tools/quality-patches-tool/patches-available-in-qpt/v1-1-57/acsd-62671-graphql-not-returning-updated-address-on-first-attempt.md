---
title: ACSD-62671： [!DNL GraphQL] 第一次嘗試時未傳回更新的位址
description: 套用ACSD-62671修補程式以修正Adobe Commerce問題，亦即 [!DNL GraphQL] 請求在第一次嘗試時未傳回最新位址資訊。
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671： [!DNL GraphQL]第一次嘗試時未傳回更新的地址

ACSD-62671修補程式修正了[!DNL GraphQL]請求在第一次嘗試時未傳回最新地址資訊的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62671。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用[!DNL GraphQL Application Server]時，客戶地址請求未傳回最新資料。

<u>要再現的步驟</u>：

1. 安裝並啟動[!DNL GraphQL Application Server]。
1. 確定已啟用`graphQL_query_resolver_result`快取型別。
1. 使用[!DNL GraphQL]來：

   * 建立客戶。
   * 產生權杖。
   * 使用Token為上述客戶建立多個地址。

1. 傳送[!DNL GraphQL]要求以取得客戶地址。
1. 新增地址給客戶。
1. 監控回應中傳回的位址計數時，多次重複步驟#4的要求。

<u>預期結果</u>：

[!DNL GraphQL]回應包含正確數量的客戶地址。

<u>實際結果</u>：

有時，[!DNL GraphQL]回應中傳回的位址數目不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
