---
title: ACSD-45675：產品匯出使用預設商店檢視範圍的類別名稱
description: ACSD-45675修補程式修正產品匯出使用預設商店檢視範圍的類別名稱的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20後，即可使用此修補程式。 修補程式ID為ACSD-45675。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# ACSD-45675：產品匯出使用預設商店檢視範圍的類別名稱

ACSD-45675修補程式修正產品匯出使用預設商店檢視範圍的類別名稱的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-45675。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯出使用預設商店檢視範圍的類別名稱。

<u>要再現的步驟</u>：

1. 在主存放區中建立自訂存放區檢視&#x200B;**[!UICONTROL Thai]**。
1. 將&#x200B;**[!UICONTROL Thai]**&#x200B;設為主要網站的預設商店檢視。
1. 在&#x200B;**[!UICONTROL Default Category]**&#x200B;下建立下列類別結構：

   *[!UICONTROL Default category/Tea/Black]*

1. 選取類別&#x200B;**[!UICONTROL Tea]**&#x200B;並將&#x200B;**[!UICONTROL Scope]**&#x200B;變更為&#x200B;**[!UICONTROL Thai]**。
1. 將&#x200B;**[!UICONTROL Category Name]**&#x200B;設為&#x200B;**[!UICONTROL ชาดำ]**。
1. 建立簡單產品&#x200B;**[!UICONTROL SP001]**&#x200B;並指派類別&#x200B;**[!UICONTROL Black]**。
1. 確定cron未執行。
1. 執行產品匯出。 依SKU篩選並選取&#x200B;**[!UICONTROL SP001]**。
1. 檢查匯出的CSV中的&#x200B;**[!UICONTROL categories]**&#x200B;欄。

<u>預期結果</u>：

匯出期間未選取任何存放區，因此您應該取得如下的類別路徑： *[!UICONTROL Default Category/Tea/Black]*。

<u>實際結果</u>：

類別路徑有混合語言： *[!UICONTROL Default Category/ชาดำ/Black]*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tools] >使用狀況](/help/tools/quality-patches-tool/usage.md) （在品質修補程式工具指南中）。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
