---
title: MDVA-42283：法文地區設定的日期 — 時間格式無效
description: MDVA-42283修補程式修正了法文地區設定的管理順序格線中的日期 — 時間格式無效的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-42283。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: CMS
role: Admin
exl-id: ed99519d-03e2-444b-9cd1-e5c6e6d2ac2d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42283：法文地區設定的日期 — 時間格式無效

MDVA-42283修補程式修正了法文地區設定的管理順序格線中的日期 — 時間格式無效的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-42283。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

法文地區設定的管理順序格線中的日期 — 時間格式無效。

<u>要再現的步驟</u>：

1. 建立訂單、客戶、CMS頁面或CMS區塊。
1. 移至&#x200B;**管理員** > **帳戶設定**，並將管理員的介面地區設定設為&#x200B;**Français （加拿大）**/**Français （加拿大）(fr_CA)**&#x200B;或&#x200B;**巴西葡萄牙文(pt_BR)**。
1. 觀察任何「訂單」、「出貨」、「銷退折讓單」、「客戶」、「CMS」頁面或CMS區塊格線之日期欄中的值。

<u>預期結果</u>：

日期採用實體實際編輯頁面上顯示的格式。

<u>實際結果</u>：

日期時間值不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
