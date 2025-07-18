---
title: ACSD-62952：店面顯示的贈品註冊日期不準確
description: 套用ACSD-62952修補程式，修正店面禮品註冊日期顯示不準確的Adobe Commerce問題。
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952：店面顯示的贈品註冊日期不準確

ACSD-62952修補程式修正店面禮品註冊日期顯示不準確的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62952。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

共用禮品登入的店面所顯示的事件日期，誤顯示為比實際日期早一天。

<u>要再現的步驟</u>：

1. 以客戶身分登入前端。
1. 在[!UICONTROL My Account]儀表板中，按一下&#x200B;**[!UICONTROL Gift Registry]**。
1. 如果沒有現有的登入，請建立登入並指定任何日期。
1. 新增任何專案至購物車。
1. 從購物車頁面，按一下&#x200B;**[!UICONTROL Add all items to Gift Registry]**。
1. 共用贈品登入。

<u>預期結果</u>：

禮品註冊顯示正確的事件日期。

<u>實際結果</u>：

從邀請電子郵件開啟的禮品註冊會將活動日期顯示為早一天。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
