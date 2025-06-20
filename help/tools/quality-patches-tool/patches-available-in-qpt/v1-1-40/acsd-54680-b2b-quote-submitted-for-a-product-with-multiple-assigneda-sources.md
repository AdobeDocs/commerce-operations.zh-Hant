---
title: ACSD-54680：無法處理具有多個指定來源之產品的B2B報價
description: 套用ACSD-54680修補程式，修正Adobe Commerce無法處理具有多指定來源之產品的B2B報價的問題。
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680：無法處理具有多個指定來源之產品的B2B報價。

ACSD-54680修補程式修正了無法處理具有多個指派來源之產品的B2B報價的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54680。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法處理具有多個指定來源之產品的B2B報價。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]**&#x200B;並建立兩個新來源： **Source 1**&#x200B;和&#x200B;**Source 2**。
1. 移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]**&#x200B;並建立新庫存： **庫存A**，將其指派至主要網站，然後將&#x200B;**Source 1**&#x200B;和&#x200B;**Source 2**&#x200B;指派至該網站。
1. 建立簡單產品，指派&#x200B;**Source 1**&#x200B;和&#x200B;**Source 2**，並為每個來源設定數量= *2*。 （因此，產品的可銷售數量應為&#x200B;*4*）。
1. 建立公司帳戶。
1. 前往&#x200B;**[!UICONTROL Storefront]**&#x200B;並登入公司帳戶。
1. 將簡單產品加入購物車，數量= *4*。
1. 開啟&#x200B;*[!UICONTROL Shopping cart]*&#x200B;並按一下&#x200B;**[!UICONTROL Request a quote]**&#x200B;按鈕。
1. 新增註解與報價名稱，然後按一下&#x200B;**[!UICONTROL Send a Request]**&#x200B;按鈕。
1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**。
1. 開啟最近提交的報價。

<u>預期結果</u>：

報價專案包含訂購的產品。

<u>實際結果</u>：

引用頁面中的專案區段是空的，因此無法處理報價。
`var/log/system.log`包含

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
