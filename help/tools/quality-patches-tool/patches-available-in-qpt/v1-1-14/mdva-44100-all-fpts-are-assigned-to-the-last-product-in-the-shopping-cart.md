---
title: MDVA-44100：所有FPT都已指派給購物車中的最後一個產品
description: MDVA-44100修補程式解決所有FPT指派給購物車中最後一個產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44100。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100：所有FPT都已指派給購物車中的最後一個產品

MDVA-44100修補程式解決所有FPT指派給購物車中最後一個產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44100。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

所有FPT都會指派給購物車中的最後一個產品，而其餘產品的FPT值則會重設。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **銷售** > **稅捐**&#x200B;並設定：
   * 啟用FPT =是
   * 沖銷稅捐至FPT =是
   * 小計中包含FPT =是
1. 移至&#x200B;**商店** > **屬性** > **產品**，然後建立型別= Fixed Product Tax的新屬性。
1. 將屬性新增至屬性集。
1. 從屬性集建立兩個產品，並設定您國家/地區和州的FPT屬性。
1. 將兩個專案新增至訂單。
1. 輸入需要支付FPT的地址。
1. 下訂單。
1. 檢查訂單上的專案清單。

<u>預期結果</u>：

FPT會顯示在每個產品下方。

<u>實際結果</u>：

兩個專案的FPT值都會顯示在第二個專案下。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
