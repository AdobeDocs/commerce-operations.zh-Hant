---
title: ACSD-46856：改善更新層級價格時的效能
description: 套用ACSD-46856修補程式，以在透過System &amp；Configuration &amp；gt；匯入&amp；gt；進階定價更新層級價格時提升效能。
feature: Orders
role: Admin
exl-id: 5c954f2c-a55c-43ba-919f-406f4b173d30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-46856：透過「系統>組態>匯入>進階訂價」更新層級價格緩慢

ACSD-46856修補程式可改善透過&#x200B;**[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**&#x200B;更新層級價格時的效能。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46856。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過&#x200B;**[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**&#x200B;更新層級價格緩慢。

<u>要再現的步驟</u>：

* 透過&#x200B;**系統** > **組態** > **匯入** > **進階定價**&#x200B;匯入大量產品（例如：10k+或200k+）。

<u>預期結果</u>：

使用修補程式，20萬多種產品的處理時間約為1:00分鐘。

<u>實際結果</u>：

若沒有修補程式，1萬多種產品的處理時間約為10:00分鐘。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
