---
title: ACSD-55339：解決Adobe Commerce可轉讓報價中的SKU微調問題
description: 套用ACSD-55339修補程式，修正Adobe Commerce中前導為0的產品SKU遭到修剪，而造成交涉錯誤的問題。
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339：解決Adobe Commerce可轉讓報價中的SKU微調問題

ACSD-55339修補程式修正了前導為0的產品SKU被裁剪，導致在交涉過程中發生錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-55339。 請注意，此問題已排程在Adobe Commerce B2B 1.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用於可轉讓報價時，會裁剪開頭為零的數位產品SKU，導致無法更新數量或設定價格的錯誤。

<u>要再現的步驟</u>：

1. 導覽至管理面板中的產品建立區段。
1. 將產品的[!UICONTROL SKU]設定為01910。
1. 登入店面並執行下列操作：
   1. 將產品新增至購物車。
   1. 檢視並編輯購物車。
   1. 要求報價。
1. 前往[!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View]和[!UICONTROL Add Products by SKU] - 01910。

**備註：** SKU顯示為&#x200B;*1910*，而非&#x200B;*01910*。 這種差異會防止使用者更新數量或設定價格，因為目錄中不存在具有SKU 1910的產品。

<u>預期結果</u>：

可轉讓報價單應順利更新，且無任何錯誤。

<u>實際結果</u>：

系統會顯示警告訊息，指出產品不存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
