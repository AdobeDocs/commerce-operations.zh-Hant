---
title: 「ACSD-58735：受限制的管理員無法在相關網站的客戶帳戶上檢視放棄的購物車」
description: 套用ACSD-58735修補程式以修正Adobe Commerce問題，該問題導致受限制的管理員無法檢視相關網站之Commerce管理員中客戶帳戶頁面上的放棄購物車。
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735：受限制的管理員無法檢視相關網站客戶帳戶上的放棄購物車

ACSD-58735修補程式修正了具有受限制角色的管理員使用者無法從Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]**&#x200B;索引標籤檢視放棄客戶購物車的問題。

發生此問題的原因在於，顯示多個網站的格線檢視時，如果「管理」面板中預設載入捨棄的購物車，則不會顯示相關的商店ID。

安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58735。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限管理員無法在管理員面板中的客戶帳戶頁面上檢視放棄的購物車。

<u>要再現的步驟</u>：

1. 建立只能存取其中一個網站的管理員角色。
1. 建立捨棄的購物車。
1. 以具有完整許可權的管理員使用者身分登入。 檢查&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**，檢視購物車是否顯示。
1. 檢查&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;是否為受限制的管理員使用者。

<u>預期結果</u>：

受限制的管理員可以看到相關網站放棄的購物車。

<u>實際結果</u>：

受限制的管理員看不到相關網站已捨棄的購物車。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
