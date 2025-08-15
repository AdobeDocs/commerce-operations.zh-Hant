---
title: ACSD-58163： [!UICONTROL Cart Price Rule]未套用相符的[!UICONTROL Customer Segment]購物車（不含優惠券代碼）的折扣
description: 套用ACSD-58163修補程式以修正Adobe Commerce問題，該問題導致[!UICONTROL Cart Price Rule]無法從無優惠券代碼的相符購物車中為訪客套用折扣。[!UICONTROL Customer Segment]
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163： [!UICONTROL Cart Price Rule]未套用相符的[!UICONTROL Customer Segment]購物車（不含優惠券代碼）的折扣

ACSD-58163修補程式修正[!UICONTROL Cart Price Rule]未套用無優惠券代碼之相符[!UICONTROL Customer Segment]購物車的折扣的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-58163。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Cart Price Rule]沒有優惠券代碼，不會從相符的[!UICONTROL Customer Segment]購物車為訪客套用折扣。

<u>要再現的步驟</u>：

1. 建立客戶區段：
   * 適用於訪客。
   * 條件為在購物車中放入一項產品。

1. 建立&#x200B;*[!UICONTROL Cart Price Rule]*：
   * 不含抵用券代碼。
   * 附帶條件以符合訪客客戶區段。

1. 建立簡單的產品。
1. 以客人身份開啟店面。
1. 新增一個簡單產品至購物車。
1. 前往購物車。

<u>預期結果</u>：

已套用&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;折扣。

<u>實際結果</u>：

未套用&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
