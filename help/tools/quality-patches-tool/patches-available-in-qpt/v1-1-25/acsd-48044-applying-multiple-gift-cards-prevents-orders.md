---
title: ACSD-48044：套用多張禮品卡可防止下訂單
description: 套用ACSD-48044修補程式，修正Adobe Commerce的問題，亦即套用多張禮品卡至多筆運送的單一訂單時，無法下訂單。
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044：套用多張禮品卡可防止下訂單

ACSD-48044修補程式修正了將多張禮品卡套用至一張有多重送貨的訂單時，無法下單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-48044。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將多張禮品卡套用至有多張出貨的單張訂單，可防止下訂單。

<u>要再現的步驟</u>：

1. 安裝全新版本的Adobe Commerce。
1. 建立價格為$100的簡單產品，以及價格為$10的另一個簡單產品。
1. 登入[!UICONTROL Admin panel]並建立兩張禮品卡。

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. 建立具有兩個地址的客戶。
1. 新增兩個產品至購物車。

   * 先新增$10的產品，然後新增$100的產品。 如果先新增$100產品，則無法重現問題。

1. 前往購物車，然後新增您建立的兩個禮品卡。
1. 在購物車頁面上按一下&#x200B;**[!UICONTROL Ship to Multiple Addresses]**。
1. 將每個產品指派至不同的地址。
1. 前往&#x200B;**[!UICONTROL Shipping information]**&#x200B;頁面。
1. 前往&#x200B;**[!UICONTROL Billing information]**&#x200B;頁面。
1. 移至&#x200B;**[!UICONTROL Review Your Order]**&#x200B;頁面，您可以在其中檢視問題。
1. 嘗試下訂單。

<u>預期結果</u>：

* 禮品卡已正確套用至總金額。
* 已下訂單。

<u>實際結果</u>：

禮卡金額混有錯誤&#x200B;*「請更正禮卡代碼。」下單時*。

* 第一個產品：

   * 移除禮卡(00GXM6SUGBLW) - $15.00
   * 移除禮品卡(02KB8M0H0GRD) - $0.00

* 第二個產品：

   * 移除禮卡(00GXM6SUGBLW) - $25.00
   * 移除禮品卡(02KB8M0H0GRD) - $35.00

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
