---
title: ACSD-61969：必須輸入以大寫或小寫設定的抵用券代碼
description: 套用ACSD-61969修補程式以修正Adobe Commerce問題，其中要求使用者輸入與設定為大寫或小寫完全相同的抵用券代碼。
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969：必須輸入以大寫或小寫設定的抵用券代碼

ACSD-61969修補程式修正使用者必須輸入優惠券代碼的問題，該代碼需完全依照其設定的大寫或小寫方式輸入。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-61969。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從後端套用優惠券時，您必須完全依照大寫或小寫的設定輸入優惠券代碼。 在建立管理員訂單時區分大小寫，但在店面時則不區分大小寫。

<u>要再現的步驟</u>：

1. 使用特定優惠券&#x200B;*[!UICONTROL Cart Price Rule]* TEST *建立*。 確定優惠券代碼為大寫。
1. 在Admin中建立訂單。
1. 將&#x200B;*test*&#x200B;新增至&#x200B;*[!UICONTROL Apply Coupon Code]*&#x200B;欄位，然後按一下欄位附近的箭頭以套用抵用券。
1. 觀察結果。

<u>預期結果</u>：

已成功套用抵用券。 抵用券欄位不區分大小寫。

<u>實際結果</u>：

未套用抵用券。 會顯示下列錯誤：

*「測試」優惠券代碼無效。 請驗證程式碼，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
