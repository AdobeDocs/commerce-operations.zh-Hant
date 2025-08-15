---
title: MDVA-39153：在管理員中重新排序時計算的折扣金額不正確
description: MDVA-39153修補程式修正了在管理員中重新排序時折扣金額計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-39153。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153：在管理員中重新排序時計算的折扣金額不正確

MDVA-39153修補程式修正了在管理員中重新排序時折扣金額計算錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-39153。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在管理員中重新訂購時計算的折扣金額不正確。

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理員** > **商店** > **組態** > **銷售** > **稅捐**。
1. 開啟在購物車中顯示稅捐之出貨稅捐。
1. 啟用並設定表格費率送貨方法($15)。
1. 為內建稅率(CA)建立稅捐規則。
1. 建立購物車價格規則，並將固定$5的折扣套用至整個購物車和運費金額。
1. 新增價格為$12的產品至購物車，然後前往購物車頁面。
1. 將折扣套用至購物車。
1. 將「預估」區段中的送貨方法設定為「統一費率」。
1. 繼續結帳，直到檢閱步驟（請勿下訂單）。
1. 前往首頁，然後返回購物車。
1. 將「預估」區段中的送貨方法變更為「表格費率」。

<u>預期結果</u>：

折扣保持不變 — $5。

<u>實際結果</u>：

折扣為$6.31。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
