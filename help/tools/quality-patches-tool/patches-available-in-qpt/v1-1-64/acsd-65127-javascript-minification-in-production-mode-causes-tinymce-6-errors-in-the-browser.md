---
title: ACSD-65127：生產模式中的JavaScript縮製造成瀏覽器發生 [!DNL TinyMCE] 6錯誤
description: 套用ACSD-65127修補程式以修正Adobe Commerce問題，此問題在生產模式中啟用JavaScript縮制導致 [!DNL TinyMCE] 6在瀏覽器主控台中產生錯誤，影響功能和使用者體驗。
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: c5b27b79dd2dc7f9b39e629756d3d5d01e019710
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# ACSD-65127：生產模式中的JavaScript縮製造成瀏覽器發生[!DNL TinyMCE] 6錯誤

ACSD-65127修補程式修正了在生產模式下啟用JavaScript縮制導致[!DNL TinyMCE] 6在瀏覽器主控台中產生錯誤，進而影響功能和使用者體驗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65127。 請注意，此問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)頁面上檢查相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在生產模式中啟用JavaScript縮制會導致[!DNL TinyMCE] 6在瀏覽器主控台中產生錯誤，影響功能和使用者體驗。

<u>要再現的步驟</u>：

1. 執行下列命令來設定組態：

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. 啟用生產模式。

```
bin/magento deploy:mode:set production
```

1. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。 在列出的任何產品上按一下&#x200B;**[!UICONTROL Edit]**，然後向下捲動至&#x200B;**[!UICONTROL Content]**&#x200B;並選取&#x200B;**[!UICONTROL Show Editor]**。

<u>預期結果</u>：

瀏覽器主控台中沒有任何JS錯誤。

<u>實際結果</u>：

js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`的瀏覽器主控台中有&#x200B;*404*&#x200B;個錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
