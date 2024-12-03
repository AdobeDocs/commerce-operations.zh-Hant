---
title: ACSD-60816： [!DNL New Relic] 由APM代理程式插入的瀏覽器監視指令碼與CSP不相容
description: 套用ACSD-60816修補程式以修正Adobe Commerce問題，該問題導致APM代理程式插入的 [!DNL New Relic] 瀏覽器監視指令碼與內容安全性原則(CSP)不相容，無法執行。
feature: Tools and External Services, Checkout
role: Admin, Developer
exl-id: d03c25e0-ed25-4877-8470-737d3499473f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-60816： APM代理程式插入的[!DNL New Relic]瀏覽器監視指令碼與CSP不相容

ACSD-60816修補程式修正了APM代理程式插入的[!DNL New Relic]瀏覽器監視指令碼不符合內容安全性原則(CSP)的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-60816。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p6

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

APM代理程式插入的[!DNL New Relic]瀏覽器監視指令碼與CSP不相容。

<u>要再現的步驟</u>：

1. 將產品新增至購物車。
1. 前往結帳。

<u>預期結果</u>：

開發人員控制檯中沒有CSP錯誤。

<u>實際結果</u>：

您會收到下列錯誤：

```
Content-Security-Policy: The page's settings blocked an inline script (script-src-elem) from being executed because it violates the following directive: "script-src 
...
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
