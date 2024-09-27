---
title: 「ACSD-52824：為公司客戶顯示的停用付款方法」
description: 套用ACSD-52824修補程式，修正公司設定中雖已停用，但公司客戶仍會看到 [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 付款方法的Adobe Commerce問題。
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824：為公司客戶顯示的停用付款方法

ACSD-52824修補程式修正了公司客戶出現[!DNL PayPal Express]、[!DNL Google Pay]和[!DNL Apple Pay]付款方法的問題，儘管已在公司設定中停用。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-52824。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

系統會為公司客戶顯示停用的付款方法。

<u>要再現的步驟</u>：

1. 設定並啟用[!DNL PayPal Express Checkout]。 導覽至&#x200B;**[!UICONTROL Basic Settings]** >選取&#x200B;**[!DNL PayPal Express Checkout]**&#x200B;並將&#x200B;**[!UICONTROL Display on Shopping Cart]**&#x200B;的選項設定為&#x200B;*是*。
1. 設定[!DNL Braintree]並透過[!DNL Braintree]啟用[!DNL Apple Pay]和[!DNL Google Pay]。
1. 導覽至「**[!UICONTROL Customers]** > **[!UICONTROL Companies]**」並建立新的公司。
1. 按一下&#x200B;**[!UICONTROL Advanced Settings]**，找到&#x200B;**[!UICONTROL Applicable Payment Methods]**&#x200B;並選擇&#x200B;**[!UICONTROL Selected Payment Methods]**。
1. 在&#x200B;**[!UICONTROL Selected Payment Methods]**&#x200B;底下，選擇已啟用且未與&#x200B;*[!DNL PayPal Express Checkout]*、*[!DNL Apple Pay]*&#x200B;或&#x200B;*[!DNL Google Pay]*&#x200B;關聯的付款方法。 例如，選取&#x200B;**[!UICONTROL Check/Money Order]**。
1. 選取適當的付款方式後，建立新客戶，並將其與先前建立的公司建立關聯。
1. 使用與公司相關聯的客戶帳戶登入，並繼續將專案新增到購物車。
1. 在結帳過程中，請注意迷你購物車、購物車和付款步驟。

<u>預期結果</u>：

迷你購物車和購物車中看不到[!DNL PayPal]和[!DNL Braintree]的付款選項。

<u>實際結果</u>：

來自[!DNL PayPal]和[!DNL Braintree]的付款選項仍會顯示在迷你購物車和購物車中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
