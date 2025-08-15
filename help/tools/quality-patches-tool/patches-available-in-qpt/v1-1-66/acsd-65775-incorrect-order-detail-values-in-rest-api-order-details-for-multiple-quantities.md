---
title: ACSD-65775：REST API訂單明細中，多個數量的'base_row_total'和'row_total'值不正確
description: 套用ACSD-65775修補程式以修正Adobe Commerce問題，亦即訂購相同料號的多筆數量時，REST API訂單詳細資料會傳回不正確的「base_row_total」和「row_total」值。
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: ce5a136dd59c52d5fa5b555b3ee74fe14d7e53a4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-65775： REST API訂單詳細資料中有多個數量的`base_row_total`和`row_total`值不正確

ACSD-65775修補程式修正訂購相同專案的多個數量時，REST API訂購詳細資料傳回不正確`base_row_total`和`row_total`值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-65775。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂購相同料號的多重數量時，訂單詳細資料REST API回應中的`base_row_total`與`row_total`會顯示單價，而非總價。

<u>要再現的步驟</u>：

1. 建立兩種簡單的產品：簡單1價格為$10，簡單2價格為$15。
1. 建立新的客戶帳戶。
1. 將simple1新增至數量為2的購物車以及數量為3的simple2。
1. 使用客戶帳戶下訂單。
1. 使用下列裝載將POST要求傳送至`/rest/V1/integration/admin/token`以取得管理權杖：

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. 使用GET要求擷取訂單詳細資料給`/rest/default/V1/orders/1`。

<u>預期結果</u>：

`base_row_total`與`row_total`應該反映以數量乘以料號價格計算出的總價(例如，2 × $10 = $20 for simple1)。

<u>實際結果</u>：

`base_row_total`和`row_total`只傳回單價（例如simple1為$10，而非$20）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
