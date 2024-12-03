---
title: MDVA-43731：將值新增到「相符的最少字詞」中時，搜尋同義字無法運作
description: MDVA-43731修補程式修正在「相符的最少字詞」中新增值時，搜尋同義字停止運作的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43731。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731：將值新增到「相符的最少字詞」中時，搜尋同義字無法運作

MDVA-43731修補程式修正在「相符的最少字詞」中新增值時，搜尋同義字停止運作的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43731。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在「最少相符字詞」中新增值後，搜尋同義字會停止運作。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce並搭配範例資料。
1. 將Elasticsearch7設定為搜尋引擎。
1. 搜尋「Jacket」一詞。 將會顯示產品清單。
1. 在&#x200B;**組態** > **目錄** > **目錄搜尋** > **要符合的最少字詞數**&#x200B;中，新增引數[4&lt;60%]。
1. 清除設定快取並重新索引。
1. 再次搜尋「Jacket」一詞，您會注意到畫面上已顯示產品清單。
1. 移至&#x200B;**行銷** > **SEO與搜尋** > **搜尋同義字**。
1. 新增下列同義字來建立搜尋同義字：jacket、bagtecs、express plus。
1. 重新索引。
1. 使用任何同義字進行產品搜尋。 例如，夾克。

<u>預期結果</u>：

您會在搜尋結果中取得與之前相同的產品清單。

<u>實際結果</u>：

搜尋結果中未顯示任何產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
