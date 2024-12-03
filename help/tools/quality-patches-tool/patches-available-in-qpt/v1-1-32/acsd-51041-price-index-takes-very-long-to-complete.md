---
title: ACSD-51041：價格指數需要很長時間才能完成
description: 套用ACSD-51041修補程式，以修正Adobe Commerce價格指數需花很長時間才能在非常大的產品組合完成的問題。
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51041：價格指數需要很長時間才能完成

ACSD-51041修補程式修正了超大型產品組合的價格指數需要很長時間才能完成的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51041。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果產品組合非常龐大，價格指數需要很長時間才能完成。

<u>要再現的步驟</u>：

1. 啟用&#x200B;*[!UICONTROL Inventory]*&#x200B;模組。
1. 擁有多個庫存來源（具有提供大部分庫存的非預設來源）。
1. 產生約200,000種產品。
1. 執行清查索引。

<u>預期結果</u>：

`deleteIndexData`僅處理唯一識別碼以最佳化效能。

<u>實際結果</u>：

`deleteIndexData`處理所有ID，這需要很長時間才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
