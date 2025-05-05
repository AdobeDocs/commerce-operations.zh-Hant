---
title: ACSD-63870：在公司狀態變更期間，客戶未正確登出
description: 套用ACSD-63870修補程式以修正公司客戶在作用中客戶工作階段期間狀態變更時無法正確登出的Adobe Commerce問題。
feature: Customers, B2B, Companies
role: Admin, Developer
source-git-commit: 3544eaef7812524a098e851ac8a2c140f33f7668
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# ACSD-63870：在公司狀態變更期間，客戶未正確登出

ACSD-63870修補程式可解決在作用中客戶工作階段中，當公司狀態變更時，公司客戶無法正確登出的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-63870。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在作用中客戶工作階段期間，當公司狀態變更時，客戶登出失敗。

<u>要再現的步驟</u>：

1. 啟用B2B功能。
1. 建立簡單的產品。
1. 建立新公司並將其標籤為&#x200B;*使用中*。
1. 以公司使用者身分登入，並將產品新增至購物車。
1. 繼續結帳，直到[!UICONTROL Shipping Address]步驟。 請勿輸入地址。
1. 移至管理員並將公司狀態變更為&#x200B;*未決核准*。
1. 返回前端並填入送貨地址。

<u>預期結果</u>：

客戶已登出。

<u>實際結果</u>：

* 使用者收到&#x200B;*發生錯誤*&#x200B;錯誤。
* `var/log/exception.log`包含：

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 安裝修補程式後所需的其他步驟

（本節為選用；套用修補程式修正問題後，可能需要執行一些步驟。） 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。

