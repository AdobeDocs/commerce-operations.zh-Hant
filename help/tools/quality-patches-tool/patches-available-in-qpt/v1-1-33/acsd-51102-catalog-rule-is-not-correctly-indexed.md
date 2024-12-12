---
title: ACSD-51102：套用至大量未正確編制索引產品的目錄規則
description: 套用ACSD-51102修補程式，修正已套用至大量產品的目錄規則在排程更新啟用規則時未正確編制索引的Adobe Commerce問題。
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102：套用至大量未正確編制索引產品的目錄規則

ACSD-51102修補程式修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51102。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

排定的更新已啟用目錄規則時，套用至大量產品的目錄規則無法正確編制索引。

先決條件：

* Cron工作已設定並每分鐘執行一次。

<u>要再現的步驟</u>：

1. 建立包含數千項產品的大型目錄，以便在啟用目錄規則時，讓&#x200B;*目錄規則*&#x200B;索引子的執行時間超過120秒。
2. 建立兩個目錄規則，*作用中*&#x200B;狀態設定為&#x200B;*否*。  例如，*測試1*&#x200B;和&#x200B;*測試2*。 每個規則都應影響目錄中的所有產品，並讓索引器執行超過120秒。
3. 確定索引子的狀態為&#x200B;*就緒*。
4. 建立排程更新以啟用這兩個規則。 *測試2*&#x200B;排程應在&#x200B;*測試1*&#x200B;後立即開始。 例如，差異為1分鐘。
5. 檢查店面的產品價格。

<u>預期結果</u>

會套用兩個規則的折扣。

<u>實際結果</u>

僅套用第一個規則折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
