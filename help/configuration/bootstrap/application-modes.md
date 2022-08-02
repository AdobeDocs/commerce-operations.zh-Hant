---
title: 應用模式
description: Commerce應用程式可以根據您的需要以不同的模式運行。 查看可用應用程式模式的詳細清單。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# 應用模式

您可以在以下任一操作中運行Commerce應用程式 _模式_:

| 模組名稱 | 說明 |
| ----------- | ----------- |
| 預設 | 使您能夠在不更改任何設定的情況下在單個伺服器上部署Commerce應用程式。 但是，未針對生產優化預設模式。<br>要在多個伺服器上部署Commerce應用程式或對其進行生產優化，請切換到其他模式之一。<ul><li>已啟用靜態視圖檔案快取</li><li>異常不顯示給用戶；而是將異常寫入日誌檔案。</li><li>隱藏自定義 `X-Magento-*` HTTP請求和響應標頭</li></ul> |
| 開發者 | 此模式僅供開發：<ul><li>禁用靜態視圖檔案快取</li><li>提供詳細記錄</li><li>啟用 [自動代碼編譯](../cli/code-compiler.md)</li><li>啟用增強的調試</li><li>顯示自定義 `X-Magento-*` HTTP請求和響應標頭</li><li>導致效能最低</li><li>顯示前端上的錯誤</li></ul> |
| 生產 | 此模式適用於在生產系統上部署：<ul><li>不向用戶顯示異常（異常僅寫入日誌）。</li><li>僅從快取中提供靜態視圖檔案。</li><li>防止自動代碼檔案編譯。 新檔案或更新的檔案不會寫入檔案系統。</li><li>**不允許在管理中啟用或禁用快取類型。** 請參閱 [啟用和禁用快取](../cli/manage-cache.md#enable-or-disable-cache-types)。</li><li>某些欄位（如管理中的「高級」和「開發人員」系統配置部分）在生產模式下不可用。</li></ul> |
| 維護 | 此模式旨在防止在更新或重新配置站點時訪問該站點：<ul><li>將站點訪問者重定向到預設 `Service Temporarily Unavailable` 的子菜單。</li><li>當站點處於維護模式時， `var/` 目錄包含 `.maintenance.flag` 的子菜單。</li><li>您可以配置維護模式以允許訪問者從指定的IP地址清單訪問。</li></ul> |

>[!INFO]
>
>[Adobe Commerce在雲基礎架構上](https://devdocs.magento.com/cloud/bk-cloud.html) 僅支援生產和維護模式。

## 預設模式

如其名稱所示，預設模式是如果未指定其他模式，Commerce的操作方式。 預設模式允許您在單台伺服器上部署Commerce應用程式，而不更改任何設定。 但是，預設模式不如生產模式那樣優化。

要在多個伺服器上部署Commerce應用程式或對其進行生產優化，請切換到其他模式之一。

在預設模式下：

- 錯誤記錄到伺服器上的檔案報告中，且從不向用戶顯示
- 靜態視圖檔案已快取
- 預設模式未針對生產環境進行優化，主要是因為 [靜態檔案](https://glossary.magento.com/static-files) 是動態生成的，而不是實例化的。 換句話說，建立靜態檔案並快取它們比使用靜態檔案建立工具生成它們對效能的影響更大。

請參閱 [設定操作模式](../cli/set-mode.md)。

## 開發人員模式

在擴展或自定義Commerce應用程式時，以開發者模式運行該應用程式。

在開發人員模式下：

- 靜態視圖檔案不快取；寫到 `pub/static` 每次調用目錄
- 未捕獲的異常顯示在瀏覽器中
- 系統登錄 `var/report` 詳細
- 安 [例外](https://glossary.magento.com/exception) 在錯誤處理程式中拋出，而不是記錄
- 在 [事件](https://glossary.magento.com/event) 無法調用訂閱伺服器

請參閱 [設定操作模式](../cli/set-mode.md)。

## 生產模式

將Commerce部署到生產伺服器時，以生產模式運行Commerce。 優化伺服器環境（如資料庫和Web伺服器）後，應運行 [靜態視圖檔案部署工具](../cli/static-view-file-deployment.md) 將靜態視圖檔案寫入 `pub/static` 的子菜單。

這通過在部署時提供所有必要的靜態檔案而不是強制Commerce在運行期間按需動態查找和複製（實體化）靜態檔案而提高了效能。

在生產模式中：

- 靜態視圖檔案未實現化，並且它們的URL會即時合成。 靜態視圖檔案從 [快取](https://glossary.magento.com/cache) 只是。
- 錯誤將記錄到檔案系統中，並且永遠不會顯示給用戶。
- 可以啟用和禁用快取類型 _僅_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en)。
- 你 _不能_ 使用Admin啟用或禁用快取類型。

## 維護模式

在維護模式下運行Commerce應用程式，以便在您完成維護、升級或配置任務時使站點離線。 在維護模式中，站點將訪問者重定向到預設 `Service Temporarily Unavailable` 的子菜單。

可以建立 [自定義維護頁](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html)，手動啟用和禁用維護模式，並配置維護模式，以允許來自授權IP地址的訪問者正常查看儲存。 請參閱 [啟用和禁用維護模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html)。

如果您在雲基礎架構上使用Commerce，則Commerce應用程式在部署階段以維護模式運行。 部署成功完成後，Commerce應用程式將返回到在生產模式下運行。 請參閱 [部署掛接](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) 的 _Commerce Cloud指南_。
