---
title: ACSD-49877：視訊自動播放在行動裝置 [!DNL Safari]上無法運作
description: 套用ACSD-49877修補程式，修正視訊直接連結至遠端視訊檔案時，視訊自動播放選項在行動裝置 [!DNL Safari] 上無法運作的Adobe Commerce問題。
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877：視訊自動播放在行動[!DNL Safari]上無法運作

ACSD-49877修正視訊直接連結至遠端視訊檔案時，行動[!DNL Safari]上的自動播放選項無法運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-49877。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將[！magento/quality-patches]套件更新至最新版本，並檢查[[!DNL Quality Patches Tool]：搜尋修補程式]上的相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當視訊直接連結至遠端視訊檔案而非串流服務時，視訊自動播放無法在行動[!DNL Safari]上運作。

<u>必要條件</u>：
已安裝[!DNL Page Builder]個模組。

<u>要再現的步驟</u>：

1. 建立新的CMS頁面，並使用[!DNL Page Builder]編輯&#x200B;**[!UICONTROL Content Value]**。
1. 將&#x200B;*Tab*&#x200B;元素加入內容中，並在&#x200B;*Tab*&#x200B;內加入&#x200B;*Video元素*。
1. 現在按一下齒輪按鈕以編輯&#x200B;*視訊元素*。
1. 將指向mp4視訊檔案的連結新增到[!UICONTROL Video URL]欄位。
1. 將&#x200B;**[!UICONTROL Autoplay]**&#x200B;欄位標籤為&#x200B;*是*。
1. 按一下&#x200B;**[!UICONTROL Save]**。
1. 使用iPhone在[!DNL Safari]上開啟最近建立的頁面。

<u>預期結果</u>

自動播放選項可使用iPhone在[!DNL Safari]上運作。

<u>實際結果</u>

使用iPhone時，自動播放選項無法在[!DNL Safari]上運作。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
