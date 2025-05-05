---
title: MDVA-33606：使用者在儲存指派給階層的CMS頁面時發生錯誤
description: MDVA-33606修補程式解決在儲存指派給階層樹狀結構的CMS頁面時，使用者收到*發現唯一條件約束違規*錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3後，即可使用此修補程式。 修補程式ID為MDVA-33606。 請注意，問題已在Adobe Commerce 2.4.3中修正。
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606：使用者在儲存指派給階層的CMS頁面時發生錯誤

MDVA-33606修補程式解決在儲存指派給階層樹狀結構的CMS頁面時，使用者收到&#x200B;*發現的唯一條件約束違規*&#x200B;錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3時，即可使用此修補程式。 修補程式ID為MDVA-33606。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1-2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

嘗試儲存指派給階層樹狀結構的CMS頁面時，使用者會收到下列錯誤訊息： *發現唯一條件約束違規*。

<u>要再現的步驟</u>：

1. 建立新的CMS頁面。 將範圍設定為「所有存放區檢視」。 這是您的CMS第1頁。
1. 建立新的存放區檢視。 這是您的商店檢視2。
1. 移至&#x200B;**內容** > **階層** >將CMS頁面1新增至階層樹狀結構。
1. 將範圍變更為存放區檢視2。
   * 取消勾選「使用父節點階層」。
   * 將CMS第1頁新增至此範圍並儲存。
1. 現在將範圍變更為預設存放區檢視。
   * 取消勾選「使用父節點階層」。
   * 將CMS第1頁新增至此範圍並儲存。
1. 移至&#x200B;**內容** > **頁面** > **新增頁面**。
   * 將頁面標示為第2頁。
   * 在網站中的頁面區段中，指派給所有商店檢視和兩個商店檢視（預設商店檢視和商店檢視2），然後按一下&#x200B;**儲存頁面**。
1. 在CMS編輯頁面中，開啟「階層」標籤。
   * 將頁面2指派給存放區檢視2節點、預設節點和所有網站節點。

<u>預期結果</u>：

您可以將CMS頁面指派給所有三個節點，而不會發生任何錯誤。

<u>實際結果</u>：

您收到下列錯誤： *發現唯一條件約束違規*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
