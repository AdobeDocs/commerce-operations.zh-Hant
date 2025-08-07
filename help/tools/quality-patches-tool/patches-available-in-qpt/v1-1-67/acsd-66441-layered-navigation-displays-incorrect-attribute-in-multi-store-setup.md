---
title: ACSD-66441：階層式導覽在多儲存設定中顯示不正確的屬性選項
description: 套用ACSD-66441修補程式來修正Adobe Commerce的問題，此問題發生在多存放區設定中，階層導覽無法正確顯示其他存放區的屬性。
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441：階層式導覽在多儲存設定中顯示不正確的屬性選項

ACSD-66441修補程式修正了階層式導覽在多重存放區設定中無法正確顯示其他存放區屬性的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66441。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

店面上的分層導覽包含其他商店的屬性值，即使這些產品在目前的商店檢視中無法使用。

<u>要再現的步驟</u>：

1. 建立次要網站、商店和商店檢視。
1. 使用自訂屬性（例如，大小）建立可設定的產品。
1. 將可設定的產品指派給主要網站和類別。
1. 重新索引所有資料。
1. 導覽至店面上的指定類別。 所有大小選項在「圖層導覽」中都會正確顯示。
1. 從主要網站取消指派兩個簡單產品，並將其指派給次要網站，或從主要網站移除它們。
1. 重新索引所有資料。
1. 重新造訪店麵類別頁面，並檢查分層導覽。

<u>預期結果</u>：

階層式導覽只會顯示指派給目前商店或網站之產品的屬性選項。

<u>實際結果</u>：

階層式導覽顯示指派給其他商店或網站之產品的屬性選項（大小）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
