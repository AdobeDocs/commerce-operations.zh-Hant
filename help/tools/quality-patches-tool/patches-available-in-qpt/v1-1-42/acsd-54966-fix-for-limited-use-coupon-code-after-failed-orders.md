---
title: ACSD-54966：修復在訂單失敗後重複使用優惠券代碼的問題
description: 套用ACSD-54966修補程式以修正Adobe Commerce問題，防止在先前失敗的訂單後，重複使用每個促銷和購物車限制的優惠券代碼。
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-54966：修復在訂單失敗後重複使用優惠券代碼的問題

ACSD-54966修補程式修正了先前訂單失敗後，無法重複使用每位客戶限定的優惠券代碼的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-54966。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p10、2.4.6 - 2.4.6-p8
* Adobe Commerce： 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

優惠券代碼僅供每位客戶單次使用，無法在先前的訂單失敗後重複使用。

<u>要再現的步驟</u>：

1. 設定購物車價格規則，其中&#x200B;*[!UICONTROL Uses per Customer]* = *1*。
1. 繼續使用指派的優惠券代碼進行購買。
1. 從管理員面板取消訂單，或在付款失敗時執行訂單。
1. 執行命令： `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. 嘗試為同一客戶使用相同優惠券代碼下後續訂單。

<u>預期結果</u>：

取消訂單或發生付款失敗後，客戶可以成功重新使用優惠券代碼進行新的購買。

<u>實際結果</u>：

客戶無法重複使用抵用券代碼。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
