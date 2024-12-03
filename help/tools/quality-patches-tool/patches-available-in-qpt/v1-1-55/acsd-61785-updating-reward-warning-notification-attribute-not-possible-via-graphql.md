---
title: ACSD-61785：無法透過GraphQL變異和REST API呼叫來更新reward_warning_notification屬性
description: 套用ACSD-61785修補程式，修正無法透過Adobe Commerce突變和REST API呼叫更新「reward_warning_notification」屬性的GraphQL問題。
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785：無法透過GraphQL變異和REST API呼叫來更新reward_warning_notification屬性

ACSD-61785修補程式修正無法透過GraphQL突變和REST API呼叫更新`reward_warning_notification`屬性的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-61785。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法透過GraphQL突變和REST API呼叫更新`reward_warning_notification`屬性。

<u>要再現的步驟</u>：

1. 檢視&#x200B;*訂閱餘額更新*&#x200B;和&#x200B;*訂閱點數到期通知*&#x200B;的GraphQL和REST API結構描述/檔案。

<u>預期結果</u>：

您可以透過GraphQL和REST API訂閱&#x200B;*獎勵餘額更新*&#x200B;以及&#x200B;*點到期通知*。

<u>實際結果</u>：

GraphQL和REST API缺少此功能。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
