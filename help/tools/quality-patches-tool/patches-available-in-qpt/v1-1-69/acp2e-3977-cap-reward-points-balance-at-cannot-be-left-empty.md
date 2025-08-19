---
title: ACP2E-3977： **[!UICONTROL Cap Reward Points Balance At]**欄位不可留空
description: 套用ACP2E-3977修補程式以修正Adobe Commerce問題，其中設定**[!UICONTROL Cap Reward Points Balance At]**欄位時，**[!UICONTROL Rewards Points Balance Redemption Threshold]**欄位無法留空，導致驗證錯誤。
feature: Configuration, Rewards
role: Admin, Developer
source-git-commit: 4fd9b66967639f3afff322bfd82e68cfb79b2138
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACP2E-3977： **[!UICONTROL Cap Reward Points Balance At]**&#x200B;欄位不可留空

ACP2E-3977修補程式修正了&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;欄位不可留空的問題，即使應允許也是如此。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACP2E-3977。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p10

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;留空會觸發驗證錯誤，即使它應該在留空時停用上限。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**」。
1. 設定&#x200B;**[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*。
1. 將&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;留空。
1. 儲存。

<u>預期結果</u>：

允許&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;的空值並停用限制。

<u>實際結果</u>：

*上限獎勵點數餘額無效。 餘額必須為正數或留空。 請驗證，然後再試一次。顯示*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
