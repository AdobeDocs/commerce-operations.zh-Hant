---
title: ACSD-60584：為一個網站建立的存取Token可存取其他網站上的資訊
description: 套用ACSD-60584修補程式，修正一個網站上為使用者建立的存取Token可存取或變更其他網站上的客戶資訊的問題。
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584：為一個網站建立的存取Token可存取其他網站上的資訊

ACSD-60584修補程式修正了允許在一個網站上為使用者建立的存取權杖存取或變更其他網站上的客戶資訊的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-60584。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在一個網站上為使用者建立的API Token可讓您存取客戶資訊、建立購物車，以及在其他網站檢視上將產品新增到購物車。

<u>要再現的步驟</u>：

1. 請確定&#x200B;**[!DNL Share Customer Accounts configuration]**&#x200B;已設為&#x200B;**[!UICONTROL Per Website]**。
1. 建立其他&#x200B;*網站*、*商店*&#x200B;和&#x200B;*商店評論*。
1. 在上一步中，在主要&#x200B;*網站*&#x200B;和&#x200B;*網站*&#x200B;上建立兩個擁有相同電子郵件的客戶。
1. 透過主要網站上的[!DNL GraphQL]產生客戶權杖。
1. 使用產生的Token傳送客戶&#x200B;**[!DNL GraphQL]**&#x200B;查詢，並在標頭中加上第二個網站，以擷取客戶資訊。
1. 觀察傳回的結果。

<u>預期結果</u>：

傳回主要&#x200B;*網站*&#x200B;的客戶資訊，因為主要&#x200B;*網站*&#x200B;的Token已在[!DNL GraphQL]查詢中使用。

<u>實際結果</u>：

系統會傳回第二個網站的客戶資訊。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
