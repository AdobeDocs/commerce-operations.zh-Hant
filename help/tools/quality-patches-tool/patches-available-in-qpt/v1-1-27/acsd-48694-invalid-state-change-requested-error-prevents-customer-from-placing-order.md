---
title: ACSD-48694：要求的狀態變更無效。錯誤導致客戶無法下訂單
description: 套用ACSD-48694修補程式以修正Adobe Commerce問題，其中錯誤*請求的無效狀態變更*會阻止客戶下訂單。
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694： *要求的狀態變更無效*&#x200B;錯誤導致客戶無法下訂單

ACSD-48694修補程式修正錯誤&#x200B;*要求的無效狀態變更*&#x200B;導致客戶無法下單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48694。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.37-p4， 2.4.1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤&#x200B;*要求的狀態變更無效*&#x200B;導致客戶無法下訂單。

<u>要再現的步驟</u>：

1. 在`/estimate-shipping-methods`要求期間加入一點延遲，方法是在`app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()`加入`sleep()`函式，這樣在結帳期間從送貨步驟到付款步驟期間，`/estimate-shipping-methods`要求會在`/shipping-information`之後完成。
1. 將工作階段設定為使用[!DNL Redis]搭配&#x200B;*disable_locking： 1*&#x200B;設定。
1. 開啟&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**&#x200B;並啟用&#x200B;*[!UICONTROL Persistent Shopping Cart]*。
1. 以客戶身分登入，並將產品新增至購物車。
1. 讓客戶工作階段過期。 永久性Cookie和購物車仍持續存在。
1. 現在前往結帳，新增運送地址並導覽至付款區段。
1. 返回首頁或任何其他頁面，並使用客戶帳戶登入。
1. 讓工作階段再次過期。
1. 現在直接前往結帳頁面，並導覽至付款步驟。
1. 嘗試下訂單。

<u>預期結果</u>：

* 沒有錯誤。
* 已成功下訂單，並顯示&#x200B;*感謝您*&#x200B;頁面。

<u>實際結果</u>：

顯示錯誤&#x200B;*要求的狀態變更*&#x200B;無效，但已下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
