---
title: ACSD-49433：在購物車中顯示為禮品卡小計的預設金額
description: 套用ACSD-49433修補程式以修正Adobe Commerce問題，該問題導致預設金額在購物車中顯示為金額未結禮品卡的小計。
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
exl-id: 22691e35-0491-4935-8e7c-148900706491
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-49433：在購物車中顯示為禮品卡小計的預設金額

ACSD-49433修補程式針對開啟金額的禮品卡，修正購物車中顯示預設金額為小計的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49433。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

預設金額會以小計方式顯示在有未結金額的禮品卡購物車中。

<u>要再現的步驟</u>：

1. 建立禮品卡。
1. 確定未結金額設定為&#x200B;*[!UICONTROL Yes]* （介於$50到$500之間）。
1. 前往店面上的[!UICONTROL Gift Card]產品，並從下拉式清單中選擇其他金額。
1. 指定$100的金額(USD)。
1. 填寫其他欄位並將它們新增到購物車。
1. 前往迷你購物車或購物車頁面。

<u>預期結果</u>：

小計會顯示使用者輸入的金額。

<u>實際結果</u>：

小計會顯示預設的禮品卡金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
