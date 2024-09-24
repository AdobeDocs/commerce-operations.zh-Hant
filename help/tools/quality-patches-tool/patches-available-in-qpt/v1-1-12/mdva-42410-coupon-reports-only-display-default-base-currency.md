---
title: 「MDVA-42410：抵用券報表僅顯示預設基本貨幣」
description: MDVA-42410修補程式修正了抵用券報表僅顯示基本貨幣的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42410。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42410：抵用券報表僅顯示預設基本貨幣

MDVA-42410修補程式修正了抵用券報表僅顯示基本貨幣的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42410。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

抵用券報表只會顯示預設的基本貨幣。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店檢視。
1. 為此新網站設定不同的貨幣。 例如Euro。
1. 移至&#x200B;**商店** > **匯率**，並將匯率設定為&#x200B;**歐元**。
1. 使用特定優惠券建立&#x200B;**購物車價格規則** - **測試**。
1. 前往前端，在新網站上使用&#x200B;**測試**&#x200B;優惠券下訂單。
1. 移至&#x200B;**報表** > **銷售** > **優惠券**。
1. 在「範圍」下拉式清單中選取新網站。
1. 重新整理統計資料並執行報表。

<u>預期結果</u>：

優惠券報表會將新網站的貨幣顯示為歐元。

<u>實際結果</u>：

預設基本貨幣（在此案例中為USD）用於新網站的優惠券報表中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。