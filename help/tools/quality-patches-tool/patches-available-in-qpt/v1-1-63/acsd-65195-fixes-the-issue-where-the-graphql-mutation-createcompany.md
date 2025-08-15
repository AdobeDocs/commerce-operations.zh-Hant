---
title: ACSD-65195：GraphQL「createCompany」變異傳回錯誤給沒有必要地區的國家/地區
description: 套用ACSD-65195修補程式來修正Adobe Commerce問題，此問題導致GraphQL的「createCompany」突變對不需要地區的國家/地區擲回錯誤。
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-65195：GraphQL `createCompany`突變傳回沒有必要區域的國家/地區錯誤

ACSD-65195修補程式修正[!UICONTROL GraphQL] `createCompany`突變對不需要區域的國家擲回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63時，即可使用此修補程式。 修補程式ID為ACSD-65195。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

為不需要區域的國家指定區域時，[!UICONTROL GraphQL] `createCompany`突變傳回錯誤。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL B2B Companies]**。
1. 針對不需要變異的國家/地區，傳送具有指定地區欄位的`createCompany` [!UICONTROL GraphQL]變異。 例如： [!UICONTROL country_id]： *AE*&#x200B;和[!UICONTROL region]： *Dubai*。
1. 檢查GraphQL回應。

<u>預期結果</u>：

為不需要的區域指定區域時，公司應該可以成功建立而不會傳回錯誤。

<u>實際結果</u>：

公司未建立，且會傳回以下錯誤：
`Error: Invalid value of "Dubai" provided for the region field.`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
