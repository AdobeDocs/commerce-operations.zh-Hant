---
title: AC-15223：Storefront頁面會在切換存放區後顯示快取內容
description: 套用AC-15223修補程式來修正Adobe Commerce問題，此問題發生在切換儲存後，頁面會從快取中顯示，且存放區未如預期切換。
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223：Storefront頁面會在切換存放區後顯示快取內容

AC-15223修補程式修正了交換存放區後，由於存放區切換器無法運作，而從快取中提供頁面的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為AC-15223。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

切換存放區後，會從快取中提供頁面（存放區切換器無法運作）。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**。
2. 建立新的存放區檢視。
3. 前往店面，然後嘗試切換店面檢視。

<u>預期結果</u>：

已成功切換商店檢視。

<u>實際結果</u>：

在從後端清除快取之前，不會變更標頭中的存放區檢視名稱。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
