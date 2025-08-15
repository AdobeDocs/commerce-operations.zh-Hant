---
title: ACSD-58828：伺服器端*位址為必填*訊息會顯示在任何空白的必填欄位以及使用者端驗證
description: 套用ACSD-58828修補程式以修正Adobe Commerce問題，若任何必要欄位留空，伺服器端驗證訊息*位址為必填*連同使用者端驗證訊息一併顯示。
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828：伺服器端&#x200B;*位址為必填*&#x200B;訊息會顯示在任何空白的必填欄位以及使用者端驗證

ACSD-58828修補程式修正了伺服器端驗證訊息&#x200B;*位址為必要的問題*&#x200B;若有任何必要欄位留空，則會在使用者端驗證訊息旁邊顯示。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58828。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果任何必要欄位留空，伺服器端驗證訊息&#x200B;*位址為必填*&#x200B;會連同使用者端驗證訊息一起出現。

要再現的步驟：

1. 以客戶身分登入。
1. 新增產品至購物車。
1. 繼續結帳。
1. 保持送貨地址不變。
1. 選取&#x200B;**[!UICONTROL Flat rate]**&#x200B;並選取&#x200B;**[!UICONTROL Next]**。
1. 取消核取&#x200B;**[!UICONTROL My billing and shipping address are the same]**。
1. 從下拉式清單新增地址。
1. 將任何必要欄位保留空白並選取&#x200B;**[!UICONTROL Update]**。

預期結果：

錯誤訊息會說明遺失或不正確的資訊，無法進行簽出。

實際結果：

需要錯誤&#x200B;*位址。 請輸入，然後再試一次。顯示*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
