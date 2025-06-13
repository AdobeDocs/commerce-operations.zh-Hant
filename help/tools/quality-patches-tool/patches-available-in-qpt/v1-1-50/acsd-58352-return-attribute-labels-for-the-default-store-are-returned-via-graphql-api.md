---
title: ACSD-58352：透過 [!DNL GraphQL] API傳回預設存放區的傳回屬性標籤
description: 套用ACSD-58352修補程式以修正Adobe Commerce問題，其中當在請求標頭中指定非預設存放區檢視時，會透過 [!DNL GraphQL] API傳回預設存放區的傳回屬性標籤。
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352：透過[!DNL GraphQL] API傳回預設存放區的傳回屬性標籤

ACSD-58352修補程式修正了在要求標頭中指定非預設存放區檢視時，透過[!DNL GraphQL] API傳回預設存放區的傳回屬性標籤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-58352。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

預設存放區的傳回屬性標籤是透過[!DNL GraphQL] API傳回。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL Return Merchandising Authorization]**。
1. 在預設網站下建立&#x200B;*[!UICONTROL Additional Store]*&#x200B;和&#x200B;*[!UICONTROL Store View]*。
1. 編輯&#x200B;**[!UICONTROL Reason for Return]**&#x200B;傳回屬性，並為所有存放區檢視新增標籤。
1. 建立&#x200B;*[!UICONTROL Order]*。
1. 為該訂單建立&#x200B;*[!UICONTROL Return]*。 確定&#x200B;*[!UICONTROL Return]*&#x200B;處於&#x200B;*[!UICONTROL Pending]*&#x200B;狀態。
1. 在標頭中傳送具有指定非預設[!UICONTROL Store View]的客戶[!DNL GraphQL]查詢：

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. 觀察回應。

<u>預期結果</u>

[!DNL GraphQL]回應中的傳回標籤是針對要求標頭中設定的[!UICONTROL Store View]。

<u>實際結果</u>：

[!DNL GraphQL]回應中的傳回標籤適用於預設[!UICONTROL Store View]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
