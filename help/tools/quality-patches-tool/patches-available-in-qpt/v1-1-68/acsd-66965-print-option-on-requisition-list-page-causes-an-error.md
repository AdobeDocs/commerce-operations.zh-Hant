---
title: ACSD-66965： [!UICONTROL Requisition List]頁面上的[!UICONTROL Print]選項造成錯誤
description: 套用ACSD-66965修補程式以修正Adobe Commerce中，[!UICONTROL Requisition List]頁面上的[!UICONTROL Print]選項會導致錯誤的問題。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: ccd0920a-074c-4851-a45a-09c43b04fe64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-66965： **[!UICONTROL Requisition List]**&#x200B;頁面上的&#x200B;**[!UICONTROL Print]**&#x200B;選項造成錯誤

ACSD-66965修補程式修正&#x200B;**[!UICONTROL Requisition List]**&#x200B;頁面上的&#x200B;**[!UICONTROL Print]**&#x200B;選項造成錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66965。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**[!UICONTROL Requisition List]**&#x200B;頁面上的&#x200B;**[!UICONTROL Print]**&#x200B;選項因為`Grid.php`中有null物件參考而造成錯誤。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**」。
1. 將&#x200B;**[!UICONTROL Enable Company]**、**[!UICONTROL Enable Shared Catalog]**&#x200B;和&#x200B;**[!UICONTROL Enable Requisition List]**&#x200B;設定為`Yes`。
1. 建立兩個簡單的產品。
1. 登入店面並開啟&#x200B;**[!UICONTROL My Account]**&#x200B;頁面。
1. 建立請購單清單。
1. 將兩個產品指定至請購單清單。
1. 存取請購單清單並列出產品。
1. 按一下&#x200B;**[!UICONTROL Print]**。

<u>預期結果</u>：

**[!UICONTROL Requisition List]**&#x200B;頁面上的&#x200B;**[!UICONTROL Print]**&#x200B;選項會顯示無錯誤的列印預覽。

<u>實際結果</u>：

出現下列錯誤訊息： *應用程式執行期間發生錯誤。 如需詳細資訊，請參閱例外狀況記錄檔。*

```text
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
