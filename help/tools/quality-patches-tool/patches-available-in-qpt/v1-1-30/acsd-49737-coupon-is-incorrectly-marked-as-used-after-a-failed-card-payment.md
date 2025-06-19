---
title: ACSD-49737：信用卡付款失敗後，優惠券錯誤地標籤為已使用
description: 套用ACSD-49737修補程式，以修正Adobe Commerce在支付信用卡失敗後，優惠券錯誤地標示為使用的問題。
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737：信用卡付款失敗後，優惠券錯誤地標示為&#x200B;*已使用*

ACSD-49737修補程式修正了信用卡付款失敗後，優惠券被錯誤標示為&#x200B;*已使用*&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-49737。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

信用卡付款失敗後，優惠券錯誤地標籤為&#x200B;*已使用*。

<u>必要條件</u>：

1. 設定&#x200B;**[!UICONTROL Braintree sandbox payment]**&#x200B;方法。
1. 請確定&#x200B;[*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en)消費者已設定並執行。

<u>要再現的步驟</u>：

1. 使用自動產生的優惠券代碼建立&#x200B;**[!UICONTROL Cart Price Rule]**。
1. 以客戶身分登入。
1. 將產品新增至購物車。
1. 套用自動產生的抵用券代碼。
1. 嘗試以失敗的付款下訂單。
1. 檢查&#x200B;**[!UICONTROL Manage Coupon Codes]**&#x200B;標籤下&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;中的優惠券使用方式。

<u>預期結果</u>：

如果付款失敗，則不應將優惠券標示為&#x200B;*已使用*。

<u>實際結果</u>：

* 優惠券代碼顯示 — 已使用： *是*，使用次數： *1*
* 優惠券代碼僅供一次性使用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 安裝修補程式後所需的其他步驟

（本節為選用；套用修補程式修正問題後，可能需要執行一些步驟。） 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
