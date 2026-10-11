---
title: ACSD-63578：按一下[!UICONTROL Add to Order by SKU]中的[!UICONTROL Delete]圖示不會移除SKU
description: 套用ACSD-63578修補程式以修正Adobe Commerce問題，其中在Admin中按一下[!UICONTROL Add to Order by SKU]中的[!UICONTROL Delete]圖示未移除SKU。
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '320'
ht-degree: 0%
---
# ACSD-63578：按一下&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;圖示不會移除SKU

ACSD-63578修補程式修正在Admin中按一下&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;圖示未移除SKU的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63578。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在Admin中按一下&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;圖示不會從訂單中移除SKU。

<u>要再現的步驟</u>：

1. 導覽至「管理員> **[!UICONTROL Sales]** > **[!UICONTROL Orders]**」，然後按一下&#x200B;**[!UICONTROL Create New Order]**。
1. 選擇客戶。
1. 按一下&#x200B;**[!UICONTROL Add to Order by SKU]**。
   * 輸入SKU。
   * 按一下&#x200B;**[!UICONTROL Add another]**&#x200B;按鈕。
1. 按一下&#x200B;**[!UICONTROL Delete]**&#x200B;圖示。

<u>預期結果</u>：

* 在管理員的訂單中新增及移除產品。

<u>實際結果</u>：

* **[!UICONTROL Delete]**&#x200B;圖示無法運作。
* 主控台中出現錯誤：

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
