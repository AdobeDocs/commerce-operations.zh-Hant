---
title: ACSD-66952：設定目標規則時，在每個PLP或購物車造訪時清除快取
description: 套用ACSD-66952修補程式以修正設定目標規則時，在每個PLP或購物車造訪中清除快取而導致不必要的效能開銷的Adobe Commerce問題。
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-66952：設定目標規則時，在每個PLP或購物車造訪時清除快取

ACSD-66952修補程式修正了每次PLP或購物車造訪時清除快取的問題，這會在設定目標規則時造成效能額外負荷。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66952。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

每次PLP或購物車造訪時清除快取的問題，會在設定目標規則時造成效能額外負荷。

<u>要再現的步驟</u>：

1. 產生小型範例資料集。
1. 建立目標規則值，如下所示：
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *相關產品*
      * **[!UICONTROL Status]** = *作用中*
      * **[!UICONTROL Apply to]** = *相關產品*
   1. **[!UICONTROL Products to Match]**
      * 保留為其預設值。
   1. **[!UICONTROL Products to Display]**
      * 若這些條件中的&#x200B;**全部**&#x200B;為&#x200B;*true*，請設定&#x200B;**[!UICONTROL Product Category]** = *常數值111111*
1. 開始監控快取失效要求的記錄檔。
1. 造訪產品頁面。
1. 新增產品至購物車並導覽至購物車頁面。

<u>預期結果</u>：

瀏覽網站時，應用程式不應讓快取失效。

<u>實際結果</u>：

快取標籤會失效。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
