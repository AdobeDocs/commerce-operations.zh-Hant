---
title: ACP2E-3838： [!DNL Page Builder] CORS錯誤導致無法在生產模式的管理面板中儲存變更
description: 套用ACP2E-3838修補程式以修正Adobe Commerce問題，該問題導致 [!DNL Page Builder] CORS錯誤無法在生產模式中將變更儲存在管理面板中。
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838： [!DNL Page Builder] CORS錯誤導致無法在生產模式的管理面板中儲存變更

ACP2E-3838修補程式修正了[!DNL Page Builder] CORS錯誤導致無法在生產模式的管理面板中儲存變更的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACP2E-3838。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL Page Builder] CORS錯誤導致無法在生產模式的管理面板中儲存變更。

<u>要再現的步驟</u>：

1. 登入管理面板。
1. 前往&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 按一下&#x200B;**[!UICONTROL Add New Page]**，或選取現有的CMS頁面並按一下&#x200B;**[!UICONTROL Edit]**。
1. 按一下&#x200B;**[!UICONTROL Edit with Page Builder]**&#x200B;以新增內容區塊或編輯現有區塊。
1. 對內容進行任何變更，例如新增文字、影像或其他元素。
1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕。

<u>預期結果</u>：

頁面內容應該可以成功儲存且沒有任何錯誤。

<u>實際結果</u>：

1. [!DNL Page Builder]變更無法儲存。
1. 瀏覽器主控台會記錄與CORS相關的錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
