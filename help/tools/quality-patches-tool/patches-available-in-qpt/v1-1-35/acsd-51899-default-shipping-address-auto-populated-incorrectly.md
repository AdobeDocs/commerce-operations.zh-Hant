---
title: 'ACSD-51899：預設送貨地址自動填入不正確'
description: 套用ACSD-51899修補程式，修正Adobe Commerce中預設送貨地址自動填入錯誤地址的問題。
feature: Checkout
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-51899：預設送貨地址自動填入不正確

ACSD-51899修補程式修正了預設送貨地址自動填入錯誤地址的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51899。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

預設送貨地址自動填入錯誤的地址

<u>要再現的步驟</u>：

1. 啟用送貨方式下的&#x200B;**商店取貨**。
1. 建立&#x200B;*stock*&#x200B;和&#x200B;*來源*。
1. 建立產品並將產品指派給來源。
1. 新增產品至購物車。
1. 按一下&#x200B;**繼續從迷你購物車結帳**。
1. 輸入測試電子郵件地址並選取&#x200B;**在商店中挑選**。
1. 按一下&#x200B;**選取商店**&#x200B;按鈕，然後選取商店位置。
1. 按一下&#x200B;**下一步**&#x200B;按鈕。
1. 按一下商店標誌，瀏覽至&#x200B;**首頁**。
1. 開啟&#x200B;**迷你購物車**。
1. 按一下名為&#x200B;**檢視和編輯購物車**&#x200B;的底部超連結。
1. 按一下&#x200B;**繼續結帳**。
1. 按一下送貨頁面上的送貨按鈕。

<u>預期結果</u>

除了&#x200B;*國家/地區、地區和郵遞區號*&#x200B;之外，送貨位址列位保持空白。

<u>實際結果</u>

重新整理頁面後，預設送貨地址會自動填入&#x200B;*店內取貨*&#x200B;地址。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
