---
title: ACSD-62670： [!UICONTROL Ordered Products Report]匯出為CSV，且XML傳回404錯誤
description: 套用ACSD-62670修補程式以修正將[!UICONTROL Ordered Products Report]匯出為CSV和XML時會擲回錯誤的Adobe Commerce問題。
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670： *[!UICONTROL Ordered Products Report]*&#x200B;匯出至CSV和XML時擲回錯誤

ACSD-62670修補程式修正將&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;匯出為CSV和XML時會擲回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62670。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;匯出至CSV和XML時會擲回錯誤。

<u>要再現的步驟</u>：

1. 前往&#x200B;*管理員*&#x200B;面板，並導覽至&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**。
1. 嘗試匯出CSV或Excel檔案。

<u>預期結果</u>：

匯出報告時不會發生錯誤。

<u>實際結果</u>：

匯出&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;導致錯誤404。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
