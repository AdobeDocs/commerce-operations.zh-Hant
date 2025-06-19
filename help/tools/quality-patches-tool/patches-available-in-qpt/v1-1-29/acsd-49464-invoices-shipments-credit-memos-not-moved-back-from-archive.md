---
title: ACSD-49464：未從封存移回的商業發票、出貨及銷退折讓單
description: 套用ACSD-49464修補程式，以修正當訂單ID不同時，商業發票、出貨及銷退折讓單不會從封存移回的Adobe Commerce問題。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464：未從封存移回的商業發票、出貨及銷退折讓單

當orderId不同時，ACSD-49464修補程式會修正商業發票、出貨及銷退折讓單不會從封存移回的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49464。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當orderId不同時，不會將商業發票、出貨及銷退折讓單從存檔移回。

<u>要再現的步驟</u>：

1. 啟用訂單、商業發票、出貨及銷退折讓單存檔。
1. 建立並完成訂單，包括出貨、商業發票及銷退折讓單。
1. 請確認出貨、商業發票及銷退折讓單ID與訂單編號不同。
1. 將訂單移至封存。
1. 將已封存的訂單還原至訂單管理。
1. 檢查各個[!UICONTROL Invoice]、[!UICONTROL Shipping]和[!UICONTROL Credit Memo]網格頁面下的發票、送貨和銷退折讓單詳細資料。

<u>預期結果</u>：

將訂單從封存清單移至訂單管理時，會還原原始相關記錄。

<u>實際結果</u>：

* 如果所有識別碼不同，則沒有出貨、商業發票及銷退折讓單的記錄。
* 如果訂單與相關記錄具有相同的ID，則會傳回記錄。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
