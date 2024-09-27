---
title: 'ACSD-51819：使用單引號ID下多份訂單'
description: 套用ACSD-51819修補程式，修正Adobe Commerce中可透過相同報價識別碼下多份訂單的問題。
feature: Orders, Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51819：使用單引號ID下多份訂單

ACSD-51819修補程式修正了可透過相同報價識別碼下多份訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41時，即可使用此修補程式。 修補程式ID為ACSD-51819。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您可以使用相同的報價識別碼來訂購多份訂單。

<u>要再現的步驟</u>：

1. 以使用者身分登入。
1. 將專案新增到購物車並繼續結帳。
1. 選擇任何付款方式，但不要按一下&#x200B;**[!UICONTROL Place Order]**&#x200B;按鈕。
1. 在其他瀏覽器中登入相同的帳戶。
1. 繼續使用相同的專案結帳，而不需按一下&#x200B;**[!UICONTROL Place Order]**&#x200B;按鈕。
1. 同時在兩個系統中按一下&#x200B;**[!UICONTROL Place Order]**&#x200B;按鈕。
1. 驗證在兩個瀏覽器中下單的訂單。

<u>預期結果</u>：

系統只會成功處理從單一瀏覽器下出的第一筆訂單。

<u>實際結果</u>：

兩個瀏覽器均已下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
