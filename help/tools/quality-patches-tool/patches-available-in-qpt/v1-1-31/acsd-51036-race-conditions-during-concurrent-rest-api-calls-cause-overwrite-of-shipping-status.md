---
title: ACSD-51036：同時REST API呼叫期間的競爭條件會導致出貨狀態覆寫
description: 套用ACSD-51036修補程式以修正Adobe Commerce問題，此問題會在同時REST API呼叫期間發生競爭狀況，導致訂購專案表格中的出貨狀態遭到覆寫。
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036：同時REST API呼叫期間的競爭條件會導致訂購料號表格中的出貨狀態覆寫

ACSD-51036修補程式修正了同時REST API呼叫期間的競爭條件導致訂購專案表格中出貨狀態覆寫的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.31時，即可使用此修補程式。 修補程式ID為ACSD-51036。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

同時REST API呼叫期間的競爭條件會導致訂購料號表格中的出貨狀態遭到覆寫。

<u>要再現的步驟</u>：

1. 建立含有兩個專案的訂單。
1. 商業發票專案A。
1. 當您傳送料號B的出貨請求時，同時透過REST API傳送料號A的退款請求。
1. 移至&#x200B;**[!UICONTROL Admin Panel]**&#x200B;中的訂單。

<u>預期結果</u>

*[!UICONTROL Items]*&#x200B;排序資料表中專案B應有&#x200B;*[!UICONTROL Shipped 1]*&#x200B;狀態。

<u>實際結果</u>

*[!UICONTROL Items]*&#x200B;排序資料表中專案B的&#x200B;*[!UICONTROL Shipped 1]*&#x200B;狀態不存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
