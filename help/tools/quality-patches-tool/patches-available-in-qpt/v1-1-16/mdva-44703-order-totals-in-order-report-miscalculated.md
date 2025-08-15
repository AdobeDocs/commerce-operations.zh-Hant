---
title: MDVA-44703：訂單報表中的訂單總計計算錯誤
description: MDVA-44703修補程式修正限制管理員使用者的「訂單」報表中訂單總計計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16後，即可使用此修補程式。 修補程式ID為MDVA-44703。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703：訂單報表中的訂單總計計算錯誤

MDVA-44703修補程式修正限制管理員使用者的「訂單」報表中訂單總計計算錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16時，即可使用此修補程式。 修補程式ID為MDVA-44703。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限制管理員使用者的「訂單」報表中的訂單總計計算錯誤。

<u>要再現的步驟</u>：

1. 建立具有兩個商店的其他網站。
1. 建立僅能存取新網站的受限管理員使用者。
1. 以受限制的管理員使用者身分登入。
1. 使用不同的總計建立兩個訂單，每個新商店各一個。
1. 建立訂單的商業發票。
1. 移至&#x200B;**報表** > **銷售**&#x200B;並開啟&#x200B;**訂單報表**。
1. 重新整理統計資料。
1. 檢視每個商店的報告。

<u>預期結果</u>：

銷售總計對應於每個商店的訂單金額。

<u>實際結果</u>：

系統會顯示每個商店在整個網站的總銷售額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
