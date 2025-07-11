---
title: ACSD-51792：頁面沒有曝光事件
description: 套用ACSD-51792修補程式，修正啟用Adobe Commerce Tag Manager 4時頁面沒有曝光事件的Google效能問題。
exl-id: f9465a44-2c65-4af0-b949-1fe1f4a942ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-51792：頁面沒有曝光事件

ACSD-51792修補程式修正啟用[!DNL Google Tag Manager] 4時頁面沒有曝光事件的效能問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51792。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用[!DNL Google Tag Manager] 4時，頁面沒有曝光事件。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**」。
1. 設定&#x200B;**[!DNL GoogleTag Manager]**&#x200B;整合。
1. 移至[Google標籤小幫手](https://tagassistant.google.com/)，並完成連線至網站所需的步驟。
1. 開啟店面上有產品清單的類別頁面。
1. 在「標籤助理觀察」中檢查曝光數事件。

<u>預期結果</u>：

曝光事件應該從頁面上的所有產品開始。

<u>實際結果</u>：

此頁面在標籤助理觀察器中沒有曝光事件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
