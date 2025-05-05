---
title: ACSD-61103：客戶透過API成功登入後，失敗計數不會重設為零
description: 套用ACSD-61103修補程式來修正Adobe Commerce問題，即客戶透過API端點成功登入後，「customer_entity」表格中的失敗計數未重設為零。
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
source-git-commit: acb5ff9656d7391de1e9b936909ce5a8a73d5d67
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103：客戶透過API成功登入後，失敗計數不會重設為零

ACSD-61103修補程式解決客戶透過API端點成功登入後，`customer_entity`表格中的失敗計數未重設為零的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61103。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使客戶透過API端點成功登入，`customer_entity`表格中的失敗計數也不會重設為零。

<u>要再現的步驟</u>：

1. 建立客戶帳戶。
1. 使用不正確的詳細資料，透過API產生客戶Token。
1. 檢查上方客戶之`customer_entity` DB表格中的`failures_num`欄。
1. 使用正確的詳細資料，透過API產生客戶Token。
1. 檢查上方客戶之`customer_entity` DB表格中的`failures_num`欄。

<u>預期結果</u>：

使用正確的認證透過API產生客戶權杖後，`failures_num`欄應該重設為0。

<u>實際結果</u>：

使用正確的認證透過API產生客戶權杖後，`failures_num`欄未重設為0。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
