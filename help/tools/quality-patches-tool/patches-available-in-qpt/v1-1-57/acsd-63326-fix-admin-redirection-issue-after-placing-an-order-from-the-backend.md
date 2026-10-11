---
title: ACSD-63326：從後端下訂單後，修正管理員重新導向問題
description: 套用ACSD-63326修補程式以修正Adobe Commerce問題，其中管理員在後端下訂單後會重新導向至中斷頁面。
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-63326：從後端下訂單後，修正管理員重新導向問題

ACSD-63326修補程式修正了從後端下訂單後，管理員會重新導向至中斷頁面的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-63326。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

成功從後端為客戶下訂單後，管理員會重新導向至版面配置中斷的頁面。

<u>要再現的步驟</u>：

1. 導覽至「管理」面板中的&#x200B;**[!UICONTROL Customers]**&#x200B;區段。
1. 選取任一客戶並按一下&#x200B;**[!UICONTROL Edit]**。
1. 在客戶詳細資料頁面上，按一下頂端功能表中的&#x200B;**[!UICONTROL Create Order]**。
1. 選取[!UICONTROL FR French]市集，並將任何可用的產品加入訂單。
1. 在結帳時填寫所需的詳細資料，然後按一下&#x200B;**[!UICONTROL Get shipping methods and rates]**。
1. 按一下&#x200B;**[送出訂單]**&#x200B;即可下訂單。

<u>預期結果</u>：

系統會將管理員重新導向至訂單確認或擁有正確配置的感謝頁面。

<u>實際結果</u>：

系統會將管理員重新導向至配置損毀的頁面。 只有在重新整理頁面後，才會更正版面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
