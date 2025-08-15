---
title: ACSD-52906：解決已登入客戶快取的X-Magento-Vary Cookie問題
description: 套用ACSD-52906修補程式以修正登入客戶的X-Magento-Vary Cookie設定不正確的Adobe Commerce問題。
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906：為登入的客戶解決X-Magento-Vary Cookie問題

ACSD-52906修補程式修正登入客戶的X-Magento-Vary Cookie設定不正確的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-52906。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

X-Magento-Vary Cookie對屬於相同客戶區段的已登入客戶設定不正確，導致某些頁面的快取不正確。

<u>必要條件</u>：

Adobe Commerce Inventory management (MSI)模組已安裝並啟用。

<u>要再現的步驟</u>：

1. 設定[!DNL Varnish]或[!DNL Fastly]快取。
1. 建立新的客戶區段，並將其指派給&#x200B;*已註冊*&#x200B;的客戶。
1. 建立兩個客戶，例如customer1和customer2。
1. 清除快取。
1. 以customer1身分登入，並前往首頁。
1. 在瀏覽器上開啟無痕頁面。
1. 移至首頁以外的任何頁面。
1. 以customer2身分登入。
1. 移至首頁。
1. 檢查是否已在瀏覽器開發主控台中快取頁面。

<u>預期結果</u>：

頁面會從快取中擷取。

<u>實際結果</u>：

不會快取頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
