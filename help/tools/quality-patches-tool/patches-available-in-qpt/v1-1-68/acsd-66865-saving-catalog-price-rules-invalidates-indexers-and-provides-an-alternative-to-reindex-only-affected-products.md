---
title: ACSD-66865：儲存[!UICONTROL Catalog Price Rule]會使索引子失效，並提供僅重新索引受影響產品的替代方式
description: 套用ACSD-66865修補程式來修正Adobe Commerce問題，其中儲存[!UICONTROL Catalog Price Rules]會使索引子失效，並提供僅重新索引受影響產品的替代方案。
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
exl-id: 68baf176-ee6e-4ba8-8a34-8adb8d1e16fe
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-66865：儲存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;會使索引子失效，並提供僅重新索引受影響產品的替代方式

ACSD-66865修補程式修正儲存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;會使索引子失效的問題，並提供僅重新索引受影響產品的替代方法。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66865。 請注意，此問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

儲存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;會導致所有索引器失效，觸發完整重新索引，而不是只重新索引受影響的產品。

<u>要再現的步驟</u>：

1. 請確定cron未執行，且所有索引子都設定為依排程更新（除了可在儲存時更新的`customer_grid`）。
2. 使用下列命令執行完整手動重新索引： `php bin/magento indexer:reindex`。
3. 驗證所有索引是否顯示狀態&#x200B;*[!UICONTROL Ready]*，待處理專案中有&#x200B;*0*&#x200B;個專案。
4. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**。 為單一產品建立使用中的目錄價格規則（例如，使用&#x200B;*SKU*&#x200B;條件）。
5. 執行命令： `php bin/magento indexer:status`以檢查索引器狀態。
6. 請注意，即使只有一個產品受到影響，多個索引仍會標示為&#x200B;**[!UICONTROL Reindex Required]**。

<u>預期結果</u>：

僅會識別受影響的產品資料，並觸發部分重新索引，而非所有索引器的完整重新索引。

<u>實際結果</u>：

所有索引子都會觸發完整重新索引，即使只有單一產品受&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;影響亦然。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
