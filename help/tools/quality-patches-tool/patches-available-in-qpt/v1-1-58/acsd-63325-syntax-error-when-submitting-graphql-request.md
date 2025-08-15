---
title: ACSD-63325：語法錯誤：提交空的 [!DNL GraphQL] 請求時出現非預期的&amp；lt；EOF&amp；gt；錯誤
description: 套用ACSD-63325修補程式，以修正提交空的 [!DNL GraphQL] 請求時發生語法錯誤的Adobe Commerce問題。
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325：提交空白[!DNL GraphQL]請求時出現「語法錯誤：未預期&lt; EOF >」錯誤

ACSD-63325修補程式修正了提交空的[!DNL GraphQL]請求時，「語法錯誤：未預期&lt; EOF >」錯誤和非200回應代碼傳回的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63325。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

提交空的[!DNL GraphQL]請求時，出現HTTP內部伺服器錯誤，而非200回應代碼。

<u>要再現的步驟</u>：

1. 傳送空的GraphQL請求

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>預期結果</u>：

請求的回應代碼為200。

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>實際結果</u>：

發生500內部伺服器錯誤，如下所示：

```
HTTP/1.1 500 Internal Server Error
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
