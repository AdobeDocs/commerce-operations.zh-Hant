---
title: MDVA-42689：匯入期間更新產品類別時，使用者發生完整性條件約束違規錯誤
description: MDVA-42689修補程式可解決使用者在匯入期間更新產品類別時，收到「完整性條件約束違規」錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42689。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689：匯入期間更新產品類別時，使用者發生完整性條件約束違規錯誤

MDVA-42689修補程式可解決使用者在匯入期間更新產品類別時，收到「完整性條件約束違規」錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42689。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在匯入期間更新產品類別時，Adobe Commerce擲回完整性限制違規範誤。

<u>要再現的步驟</u>：

1. 設定兩個網站。
1. 在類別頁面上，在根類別底下建立最多兩個層級的子類別。 例如，根類別> **齒輪** > **監視**。
1. 建立兩個簡單的產品，並將兩個產品指派給相同的&#x200B;**齒輪** > **手錶**&#x200B;類別。
1. 將一項簡單產品指派給兩個網站。
1. 儲存產品。
1. 準備CSV檔案以供匯入。 應該有兩個產品記錄具有不同的商店檢視。 其中一個產品應同時屬於這兩個商店檢視。
1. 現在請瀏覽至&#x200B;**系統** > **匯入** > **實體型別** （產品），以匯入CSV檔案。

<u>預期結果</u>：

匯入CSV檔案時沒有發生任何錯誤。

<u>實際結果</u>：

Adobe Commerce擲回以下錯誤：

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
