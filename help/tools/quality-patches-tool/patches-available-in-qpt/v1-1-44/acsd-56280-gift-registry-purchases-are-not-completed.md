---
title: ACSD-56280：禮品註冊購買未完成
description: 套用ACSD-56280修補程式，修正未完成購買禮品註冊的Adobe Commerce問題
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280：禮品註冊購買未完成

>[!NOTE]
>
>此修補程式已由[ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md)取代。

ACSD-56280修補程式修正了禮品註冊購買未完成的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-56280。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

禮品註冊購買未完成。

<u>要再現的步驟</u>：

1. 以客戶身分登入，並將&#x200B;**[!UICONTROL product]**&#x200B;新增至贈品登入。
1. 共用禮品登入連結。
1. 在另一個瀏覽器/無痕視窗中開啟贈品登入連結。
1. 新增數量，並將專案新增至購物車。
1. 移至&#x200B;**[!UICONTROL Checkout Page]**，選取&#x200B;**[!UICONTROL shipping method]** （因為已選取送貨地址，由註冊者提供）。
1. 選取付款方式。
1. 按一下「下訂單」按鈕。

<u>預期結果</u>：

應該下訂單。

<u>實際結果</u>：

未下訂單，顯示的錯誤為`Call to a member function getUpdatedQty() on null`。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
