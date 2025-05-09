---
title: ACSD-64592：非預設商店禮品卡宣告連結重新導向至預設網站
description: 套用ACSD-64592修補程式以修正多網站設定中，從次要（非預設）網站購買虛擬禮卡時，電子郵件中的禮卡代碼連結會有預設網站URL的問題。
feature: Gift, Products
role: Admin, Developer
source-git-commit: 39866e1cf8f2afd892c9e151259a446d0277d58f
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# ACSD-64592：非預設商店禮品卡宣告連結重新導向至預設網站

ACSD-64592修補程式可修正多網站環境中，如果從次要（非主要）網站購買虛擬禮品卡，包含禮品卡代碼連結的電子郵件會將使用者導向至預設網站的URL的問題。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在多網站設定中，從次要（非預設）網站購買虛擬禮卡時，包含禮卡代碼連結的電子郵件會將使用者導向至預設網站的URL。

<u>要再現的步驟</u>：

1. 建立次要網站、商店和商店檢視。
1. 為基本網站和次要網站設定不同的基本URL。
1. 建立包含某些數量選項的虛擬禮品卡。
1. 在&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**&#x200B;產生新的程式碼集區。
1. 在次要網站上訂購禮品卡產品。
1. 在Commerce管理員中開立訂單發票。
1. 檢查&#x200B;*的禮品卡代碼連結中的URL您已收到兩封*&#x200B;電子郵件寄來的禮物。

<u>預期結果</u>：

禮卡代碼連結應具有第二個網站的連結。

<u>實際結果</u>：

即使訂單位於第二個網站，禮卡代碼連結仍具有預設的網站URL。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：
* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
