---
title: 'MDVA-42326：工作階段逾時後，客戶在結帳時發生錯誤'
description: MDVA-42326修補程式可解決客戶在工作階段逾時後結帳時發生錯誤（即使已啟用永久購物車）的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-42326。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326：工作階段逾時後，客戶在結帳時發生錯誤

MDVA-42326修補程式可解決客戶在工作階段逾時後結帳時發生錯誤（即使已啟用永久購物車）的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-42326。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使永久購物車已啟用，客戶在工作階段逾時後結帳時也會發生錯誤。

<u>必要條件</u>：

1. 移至&#x200B;**設定** > **一般** > **網頁** > **預設Cookie設定** > **Cookie期限**，並設定為&#x200B;**120**。
1. 移至&#x200B;**設定** > **客戶** > **客戶設定** > **線上客戶選項**，並將兩個值設定為&#x200B;**2**。
1. 移至&#x200B;**設定** > **客戶** > **永久購物車**，並設定為&#x200B;**啟用**。
1. 移至&#x200B;**設定** > **銷售** > **付款方式**，並關閉&#x200B;**支票/匯票**&#x200B;以外的所有付款方式（應該啟用）。

<u>要再現的步驟</u>：

1. 以客戶身分登入，並將一些產品新增到購物車。
1. 檢查購物車。
1. 等候兩分鐘（在先決條件中設定）；工作階段應逾時。
1. 按一下&#x200B;**前往簽出**，並且不要重新整理頁面。
1. 以客人身份結帳，填寫運送地址並選擇運送方式。
1. 按一下&#x200B;**下一步**。
1. 在&#x200B;**檢閱與付款**&#x200B;頁面上，按一下&#x200B;**下訂單**。 由於僅允許一種付款方式，因此客戶應能在不選取付款方式的情況下下訂單。

<u>預期結果</u>：

客戶應該能夠下訂單。

<u>實際結果</u>：

客戶收到下列錯誤： *地址驗證失敗：電子郵件的格式錯誤*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
