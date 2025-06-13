---
title: MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作
description: MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作

MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用中繼更新時，Visual Merchandiser的「依規則比對產品」功能無法正確篩選產品。

<u>要再現的步驟</u>：

1. 建立任何現有產品的排程更新。
   * 為`entity_id`和`row_id`設定不同的值。
1. 建立新的可設定產品，然後建立簡單的產品（因此新產品`entity_id`和`row_ids`也不同）。
   * 為了更輕鬆複製問題，請為簡單產品設定可區分的數量值，例如5000。
1. 移至類別> **類別**&#x200B;中的產品，並啟用&#x200B;**依規則比對產品**。
1. 現在選取「數量」作為屬性，「大於」作為運運算元，「4500」作為值。
1. 按一下&#x200B;**儲存**。

<u>預期結果</u>：

隨即列出新建立的可設定產品。

<u>實際結果</u>：

新建立的可設定產品未列出。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
