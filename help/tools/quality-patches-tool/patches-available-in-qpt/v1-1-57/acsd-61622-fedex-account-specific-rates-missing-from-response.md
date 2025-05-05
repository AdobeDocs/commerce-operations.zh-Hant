---
title: ACSD-61622： REST API回應中缺少 [!DNL FedEx] 帳戶特定費率
description: 套用ACSD-61622修補程式以修正REST API回應中缺少 [!DNL FedEx] 帳戶特定費率的Adobe Commerce問題。
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622： REST API回應中缺少[!DNL FedEx]帳戶特定費率

ACSD-61622修補程式解決了REST API回應中缺少[!DNL FedEx's]帳戶特定速率的問題。 它會將`ACCOUNT`速率要求型別新增至從Adobe Commerce傳送至[!DNL FedEx]的REST API要求，這會傳回類似於SOAP API回應的回應。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-61622。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

REST API回應中缺少[!DNL FedEx's]帳戶特定費率。

<u>要再現的步驟</u>：

1. 安裝乾淨的Adobe Commerce執行個體。
1. 建立輕巧的產品，重量只有5磅。
1. 為REST API設定[!DNL FedEx]。
1. 啟用[!DNL FedEx]送貨方法並清除快取。
1. 開始觀察記錄檔： `var/log/shipping.log`
1. 新增簡單產品至購物車，並在結帳時前往送貨頁面。 客戶資料範例：

   * 郵遞區號： 58601
   * 姓名：John Doe
   * 地址： 196 Eulalia Burg
   * 國家/地區：美國
   * 州立大學：北達科他州
   * 電話號碼：187-563-3627

<u>預期結果</u>：

在REST API回應中可以使用`PAYOR_ACCOUNT_PACKAGE`速率，類似於SOAP API回應。

<u>實際結果</u>：

回應中只有`PAYOR_LIST_PACKAGE`費率可用，這表示沒有來自[!DNL FedEx]的交涉（帳戶）費率。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
