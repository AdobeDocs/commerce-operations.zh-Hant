---
title: ACSD-57854： *GraphQL*回應包含停用的類別，這些類別不應列在類別彙總中
description: 套用ACSD-57854修補程式以修正Adobe Commerce問題，其中的*GraphQL*回應包含不應列在類別彙總中的停用類別。
feature: GraphQL
role: Admin, Developer
exl-id: 216aad2a-f470-49f9-b8ca-79107ca07891
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57854： *GraphQL*&#x200B;回應包含停用的類別，這些類別不應列在類別彙總中

ACSD-57854修補程式修正&#x200B;*GraphQL*&#x200B;回應包含不應該列在類別彙總中的停用類別的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-57854。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*GraphQL*&#x200B;回應包含不應該列在類別彙總中的停用類別。

<u>要再現的步驟</u>：

1. 建立兩個類別。
1. 建立產品(測試Adobe產品)並將產品指派給這兩個類別。
1. 停用已建立的其中一個類別。
1. 使用產品&#x200B;*GraphQL*&#x200B;來搜尋產品。
1. 檢查&#x200B;*GraphQL*&#x200B;回應中的產品類別清單。

<u>預期結果</u>：

停用的類別未列在&#x200B;*GraphQL*&#x200B;回應中。

<u>實際結果</u>：

停用的類別會列在類別彙總&#x200B;*GraphQL*&#x200B;回應中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
