---
title: ACSD-66049：非英文店面會因為ICU的資料庫版本而顯示不正確的定價
description: 套用ACSD-66049修補程式，修正非英文店面在舊版PHP環境（版本63.1到74.1）中由於ICU程式庫版本不符而顯示錯誤定價的Adobe Commerce問題。
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: da11e8bd5c4937ec2a7e548ce487797b83f8fd27
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-66049：非英文店面會因為ICU的資料庫版本而顯示不正確的定價

ACSD-66049修補程式修正了在舊版PHP環境（版本63.1到74.1）中，由於ICU程式庫版本不符，非英文店面顯示錯誤定價的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為ACSD-66049。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5-p3 - 2.4.5-p13、2.4.7 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用較舊的PHP ICU程式庫版本（63.1到74.1）時，非英文的店面會顯示不正確的定價。

<u>要再現的步驟</u>：

1. 檢查ICU版本：
   * 透過SSH連線到伺服器並執行命令： `php -a`
   * 出現提示時，輸入： `echo INTL_ICU_VERSION;`
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**。**[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*。
1. 建立價格= 100的產品。
1. 檢視店面的產品頁面。

<u>預期結果</u>：

顯示的價格不是0。

<u>實際結果</u>：

短暫顯示為100後，價格會立即更新為0。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
