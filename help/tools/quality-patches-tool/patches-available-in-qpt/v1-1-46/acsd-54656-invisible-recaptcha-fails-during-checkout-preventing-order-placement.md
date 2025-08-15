---
title: 隱藏的 [!DNL reCAPTCHA] 在結帳時失敗，無法下訂單
description: 套用ACSD-54656修補程式，修正結帳期間不可見的 [!DNL reCAPTCHA] 無法正常運作（導致訂單無法下達）的Adobe Commerce問題。
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656：隱藏的[!DNL reCAPTCHA]在結帳期間無法正常運作，導致訂單無法下達。

ACSD-54656修補程式修正隱藏的[!DNL reCAPTCHA]在結帳期間無法正常運作，導致無法下訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46時，即可使用此修補程式。 修補程式ID為ACSD-54656。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

隱藏的[!DNL reCAPTCHA]在結帳期間無法正常運作，導致訂單無法下達。

<u>要再現的步驟</u>：

1. 在[!DNL reCAPTCHA]頁面上啟用禮品卡的任何型別[!UICONTROL Checkout]。
1. 將產品加入購物車並移至&#x200B;**[!UICONTROL Checkout]**&#x200B;頁面。
1. 展開禮卡表單，並填寫有效的禮卡優惠券。
1. 按一下&#x200B;**[!UICONTROL See balance and apply]**&#x200B;按鈕。

<u>預期結果</u>：

已成功套用禮品卡。

<u>實際結果</u>：

顯示錯誤訊息： *[!DNL reCAPTCHA]驗證失敗，請再試一次*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
