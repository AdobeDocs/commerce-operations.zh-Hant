---
title: ACSD-62591：設定**[!UICONTROL User Agent Rules]**時，主題不會切換
description: 套用ACSD-62591修補程式，修正設定**[!UICONTROL User Agent Rules]**時主題未正確切換的Adobe Commerce問題。
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591：設定[!UICONTROL User Agent Rules]時主題未正確切換

ACSD-62591修補程式修正設定&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;時主題未正確切換的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-62591。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設定&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;時，主題未正確切換。

<u>要再現的步驟</u>：

1. 開啟Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**。
1. 編輯商店檢視主題。
1. 在&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;中設定`/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i`並選擇不同的主題。
1. 儲存變更並清除快取。
1. 在行動裝置上開啟店面頁面。
1. 從案頭瀏覽器開啟相同頁面。

<u>預期結果</u>：

案頭瀏覽器和行動裝置會使用各自的主題來顯示頁面。

<u>實際結果</u>：

案頭瀏覽器會顯示具有行動佈景主題的快取頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。

