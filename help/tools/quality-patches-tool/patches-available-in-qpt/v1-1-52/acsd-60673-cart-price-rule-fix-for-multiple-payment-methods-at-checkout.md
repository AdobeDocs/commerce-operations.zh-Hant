---
title: ACSD-60673：在結帳時針對多個付款方式修正了[!UICONTROL Cart Price Rule]個問題
description: 套用ACSD-60673修補程式來修正Adobe Commerce問題，使用付款方式條件的[!UICONTROL Cart Price Rule]的折扣不一定會列在總計中。
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673：在結帳時針對多個付款方式修正了[!UICONTROL Cart Price Rule]個問題

ACSD-60673修補程式修正使用付款方式條件的[!UICONTROL Cart Price Rule]的折扣不一定會列在總計中的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-60673。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳時多個付款方式的[!UICONTROL Cart Price Rule]未正確套用至特定的付款方式。

<u>必要條件</u>

確定在&#x200B;**[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]**&#x200B;和&#x200B;**[!UICONTROL Bank Transfer]**&#x200B;中已啟用。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL Multiple Payment Methods]**。
1. 建立&#x200B;*[!UICONTROL Cart Price Rule]*。
   * 設定&#x200B;**[!UICONTROL Conditions]**：付款方式為&#x200B;**[!UICONTROL Money Order]** （或銀行轉帳）
   * 選取&#x200B;**[!UICONTROL Actions]** =所有產品的&#x200B;*25%*&#x200B;折扣
1. 建立虛擬產品。
1. 若要複製新的報價和訪客客戶&#x200B;*[!UICONTROL Status]*，請前往店面並清除Cookie。
1. 將虛擬產品新增到購物車。
1. 繼續進行&#x200B;*簽出*。
1. 按一下&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;中定義的付款方式。
1. 更新您的&#x200B;*[!UICONTROL Billing Address]*。
1. 確定總金額中會顯示折扣。
1. 按一下核取方塊以變更付款方式。
1. 驗證是否顯示折扣。

<u>預期結果</u>：

按一下核取方塊以切換為適用的付款方式後，折扣會顯示在&#x200B;*總計*&#x200B;中。

<u>實際結果</u>：

折扣不會顯示在&#x200B;*總計*&#x200B;中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
