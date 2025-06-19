---
title: ACSD-61534：無法使用bin/magento config：set設定設計設定，並且鎖定的值可以透過表單操作進行更改
description: 套用ACSD-61534修補程式以修正Adobe Commerce無法使用命令「bin/magento config：set」設定設計設定，且鎖定值可透過表單操控進行變更的問題。
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534：無法使用`bin/magento config:set`設定設計組態，而鎖定的值可以透過表單操作進行變更

ACSD-61534修補程式修正了無法使用`bin/magento config:set`命令設定設計組態，以及透過表單操控變更鎖定值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-61534。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法使用`bin/magento config:set`命令設定設計組態，而鎖定的值可以透過表單操作進行變更。 使用此修補程式，無法從具有`--lock-env`或`--lock-conf`的命令列工具(CLI)中設定鎖定的值。

<u>要再現的步驟</u>：

1. 使用雲端環境變數（例如`CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`）鎖定設定值。
1. 前往&#x200B;*[!UICONTROL Admin]*&#x200B;面板。
1. 前往&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**。
1. 按一下第二列&#x200B;**[!UICONTROL Global/Main website]**&#x200B;附近的&#x200B;**[!UICONTROL Edit]**。
1. 編輯商店檢視的主題。
1. 開啟HTML標題。
1. 使用開發人員工具啟用停用的&#x200B;**[!UICONTROL Scripts and Style Sheets]**&#x200B;欄位。
1. 變更值並儲存。

<u>預期結果</u>：

無法儲存鎖定的值。

<u>實際結果</u>：

資料表`core_config_data`包含`design/head/includes`的更新值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
