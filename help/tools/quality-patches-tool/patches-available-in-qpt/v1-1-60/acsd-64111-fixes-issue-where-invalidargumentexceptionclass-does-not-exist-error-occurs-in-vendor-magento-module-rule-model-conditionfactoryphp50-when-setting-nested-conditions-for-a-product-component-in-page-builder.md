---
title: ACSD-64111：修正在 [!DNL Page Builder]中設定產品元件的巢狀條件時，*InvalidArgumentException：類別不存在*錯誤
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111：修正在[!DNL Page Builder]中設定產品元件的巢狀條件時，*InvalidArgumentException：類別不存在*&#x200B;錯誤

ACSD-64111修補程式修正在[!DNL Page Builder]中設定產品元件的巢狀條件時，`vendor/magento/module-rule/Model/ConditionFactory.php:50`中發生&#x200B;*InvalidArgumentException：類別不存在*&#x200B;錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60時，即可使用此修補程式。 修補程式ID為ACSD-64111。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法）  2.4.6 - p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在[!DNL Page Builder]產品Widget條件中新增&#x200B;*[!UICONTROL Conditions Combination]*&#x200B;時，擲回錯誤&#x200B;*InvalidArgumentException：類別不存在於/app/&lt;專案id\>/vendor/magento/module-rule/Model/ConditionFactory.php*。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員。
1. 前往&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**。
1. 新增頁面（或編輯現有頁面）。
1. 展開&#x200B;**[!UICONTROL Content]**&#x200B;區段並按一下&#x200B;**[!UICONTROL Edit with Page Builder]**。
1. 新增一列，然後新增&#x200B;**[!UICONTROL Products]** Widget。
1. 設定&#x200B;**[!UICONTROL Products]** Widget。
1. 選取&#x200B;**[!UICONTROL Select Products By]**&#x200B;下的&#x200B;**[!UICONTROL Condition]**。
1. 新增條件，並從下拉式清單中選取&#x200B;**[!UICONTROL Conditions Combination]**。

<u>預期結果</u>：

記錄檔中沒有錯誤。

<u>實際結果</u>：

紀錄中會記錄以下例外狀況：

*report.CRITICAL： InvalidArgumentException：類別不存在於vendor/magento/module-rule/Model/ConditionFactory.php:50*&#x200B;中

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
