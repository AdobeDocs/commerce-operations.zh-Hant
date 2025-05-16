---
title: ACSD-64732：未正確使用客戶區段快取協力廠商控制器
description: 套用ACSD-64732修補程式，修正Adobe Commerce中第三方控制器無法正確隨客戶區段快取的問題。
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732：未正確使用客戶區段快取協力廠商控制器

ACSD-64732修補程式修正了協力廠商控制器無法正確隨客戶區段快取的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 修補程式ID為ACSD-64732。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

第三方控制器未正確隨客戶區段一起快取。

<u>要再現的步驟</u>：

1. 前往自訂控制器(/catalog/category/vary)。
1. 移至&#x200B;**[!UICONTROL Network]**&#x200B;索引標籤並檢查&#x200B;**[!DNL X-Magento-Vary]**&#x200B;的值。

<u>預期結果</u>：

自訂控制器上的&#x200B;**[!UICONTROL X-Magento-Vary]**&#x200B;值應該相同。

<u>實際結果</u>：

**[!UICONTROL X-Magento-Vary]**&#x200B;的值不同，這會造成快取遺漏。 這表示造訪自訂控制器時無法使用先前產生的快取。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
