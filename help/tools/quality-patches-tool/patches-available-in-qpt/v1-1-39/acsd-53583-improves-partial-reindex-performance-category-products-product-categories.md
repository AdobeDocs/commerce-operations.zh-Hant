---
title: ACSD-53583：改善[!UICONTROL Category Products]和[!UICONTROL Product Categories]索引器的部分重新索引效能
description: 套用ACSD-53585修補程式，以改善「類別產品」和「產品類別」索引器的部分重新索引效能。
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-53583：改善類別產品和產品類別索引器的部分重新索引效能

ACSD-53583修補程式改善了&#x200B;*類別產品*&#x200B;和&#x200B;*產品類別*&#x200B;索引器的部分重新索引效能。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-53583。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3
* 與[!DNL Live Search]模組不相容。 若要將此修補程式套用至[!DNL Live Search]安裝，請要求額外的ACSD-55719修補程式。

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部分重新索引比完整重新索引需要更長的時間。

<u>要再現的步驟</u>：

1. 將所有索引子轉換為&#x200B;*依排程更新*。
1. 使用[!DNL Performance Toolkit] （中型設定檔）產生資料。
1. 變更所有產品和類別，使其位於索引待處理專案中，且所有索引都處於閒置狀態。
1. 執行&#x200B;*類別產品*&#x200B;和&#x200B;*產品類別*&#x200B;索引器的部分重新索引。

<u>預期結果</u>：

每個產品會呼叫一次部分重新索引，而且所需時間幾乎與完整重新索引相同，因為所有產品和類別都已變更。

<u>實際結果</u>：

每個產品會呼叫多次部分重新索引，而且比完整重新索引需要更多時間。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
