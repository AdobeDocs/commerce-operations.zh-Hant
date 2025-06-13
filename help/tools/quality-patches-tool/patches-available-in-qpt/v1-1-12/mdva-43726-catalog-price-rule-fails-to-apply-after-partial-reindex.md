---
title: MDVA-43726：部分重新索引後無法套用型錄價格規則
description: MDVA-43726修補程式修正部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43726。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726：部分重新索引後無法套用型錄價格規則

MDVA-43726修補程式修正部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43726。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在部分重新索引後，無法套用以存放區層級屬性相符為基礎的目錄價格規則。

<u>要再現的步驟</u>：

1. 設定索引器模式依排程執行。
1. 建立兩個可設定的產品屬性。 例如：顏色（視覺色票）和大小（文字色票）。
1. 使用在步驟2中建立的兩個屬性來建立可設定的產品。
1. 建立產品後，請建立&#x200B;**是/否**&#x200B;型別屬性，並讓它顯示在規則條件中。
1. 將此屬性新增至預設屬性集。
1. 建立當此屬性設定為&#x200B;**是**&#x200B;時要套用的型錄價格規則。
1. 開啟與可設定產品相關的其中一個簡單產品。
1. 變更範圍以儲存檢視並將屬性值更新為&#x200B;**是**。
1. 執行`CRON`並在前端檢查價格。
1. 執行完整重新索引。 再次檢查前端的價格。
1. 更新可設定的產品類別。
1. 執行`CRON`並在前端再次檢查價格。

<u>預期結果</u>：

目錄規則可正確套用，而不需使用增量索引器來完整重新索引。

<u>實際結果</u>：

若未執行完整重新索引，則不會套用目錄規則。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
