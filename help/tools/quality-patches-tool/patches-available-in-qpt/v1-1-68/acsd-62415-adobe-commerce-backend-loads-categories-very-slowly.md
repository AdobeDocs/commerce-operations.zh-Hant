---
title: ACSD-62415： Adobe Commerce後端載入[!UICONTROL Categories]非常慢
description: 套用ACSD-62415修補程式來修正Adobe Commerce問題，此問題發生在存在大量錨點類別時，[!UICONTROL Categories]面板中[!UICONTROL Admin]頁面的效能載入非常慢。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415：錨點類別存在時，Adobe Commerce後端載入&#x200B;**[!UICONTROL Categories]**&#x200B;的速度會非常慢

ACSD-62415修補程式修正當大量錨點類別出現時，**[!UICONTROL Categories]**&#x200B;面板中&#x200B;**[!UICONTROL Admin]**&#x200B;頁面的效能載入非常緩慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-62415。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當有大量錨點類別存在時，**[!UICONTROL Categories]**&#x200B;面板中的&#x200B;**[!UICONTROL Admin]**&#x200B;頁面載入非常慢。

<u>要再現的步驟</u>：

1. 產生3K個錨點類別。
1. 在&#x200B;**[!UICONTROL Catalog]**&#x200B;面板中開啟&#x200B;**[!UICONTROL Categories]** > **[!UICONTROL Admin]**&#x200B;頁面。

<u>預期結果</u>：

**[!UICONTROL Categories]**&#x200B;頁面會快速載入，查詢不應重複1K次。

<u>實際結果</u>：

載入需要7到20秒，而且查詢的執行次數超過1K。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
