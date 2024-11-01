---
title: 'ACSD-60234： [!DNL PayPal] 在套用折扣時顯示不正確的金額'
description: 套用ACSD-60234修補程式以修正Adobe Commerce問題，其中透過付款方式套用折扣時， [!DNL PayPal] 顯示不正確的金額。
feature: Products, Configuration
role: Admin, Developer
source-git-commit: 334e9f740b49d87fc20ee8950d85adb9612c00b7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234：套用折扣時，[!DNL PayPal]顯示不正確的金額

ACSD-60234修補程式修正透過付款方式套用折扣時，[!DNL PayPal]顯示不正確金額的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-60234。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過付款方式套用折扣時，[!DNL PayPal]顯示不正確的金額。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**&#x200B;中設定&#x200B;*[!DNL PayPal Express]*。
   * [!UICONTROL Enable In-Context Checkout]可以是[!UICONTROL Yes]或[!UICONTROL NO]，此問題會在兩種情況下重現。
1. 在&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**&#x200B;中建立&#x200B;*[!UICONTROL Cart Rule]*。
   * 條件：如果所有這些條件皆為True： *[!UICONTROL Payment Method]*&#x200B;為&#x200B;*[!DNL PayPal Express Checkout]*。
   * 動作：任何動作。
1. 建立產品。
1. 前往店面，將產品加入購物車，然後前往結帳中的&#x200B;**[!UICONTROL Payment Method]**&#x200B;步驟。
1. 請確定選取&#x200B;*[!DNL PayPal Express]*&#x200B;並驗證折扣是否正確套用。
1. 按一下&#x200B;**[!DNL PayPal]**&#x200B;按鈕。
1. 登入並觀察快顯視窗的內容。

<u>預期結果</u>：

要傳遞給[!DNL PayPal]的支付金額包含購物車中的折扣。

<u>實際結果</u>：

要支付的總金額不包括折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
