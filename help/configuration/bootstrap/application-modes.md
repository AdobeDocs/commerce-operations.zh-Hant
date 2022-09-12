---
title: 應用程式模式
description: 根據您的需求，商務應用程式可以以不同模式運作。 查看可用應用程式模式的詳細清單。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# 應用程式模式

您可以在下列任一項中執行商務應用程式 _模式_:

| 模組名稱 | 說明 |
| ----------- | ----------- |
| 預設 | 可讓您在單一伺服器上部署商務應用程式，而不變更任何設定。 但是，預設模式沒有針對生產進行最佳化。<br>要在多個伺服器上部署Commerce應用程式，或為生產而優化它，請更改為其他模式之一。<ul><li>已啟用靜態檢視檔案快取</li><li>不向用戶顯示異常；而是會將例外寫入記錄檔。</li><li>隱藏自訂 `X-Magento-*` HTTP要求和回應標題</li></ul> |
| 開發人員 | 此模式僅供開發之用：<ul><li>禁用靜態視圖檔案快取</li><li>提供詳細記錄</li><li>啟用 [自動代碼編譯](../cli/code-compiler.md)</li><li>啟用增強的除錯功能</li><li>顯示自訂 `X-Magento-*` HTTP要求和回應標題</li><li>導致效能最低</li><li>在前端顯示錯誤</li></ul> |
| 生產 | 此模式用於在生產系統上部署：<ul><li>不會向使用者顯示例外（例外僅寫入記錄檔）。</li><li>僅從快取提供靜態檢視檔案。</li><li>防止自動編碼檔案編譯。 新檔案或更新的檔案不會寫入檔案系統。</li><li>**不允許您在「管理員」中啟用或停用快取類型。** 請參閱 [啟用和禁用快取](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>有些欄位（例如「管理員」中的「進階」和「開發人員」系統設定區段）在生產模式中無法使用。</li></ul> |
| 維護 | 此模式旨在防止在站點更新或重新配置時訪問該站點：<ul><li>將網站訪客重新導向至預設 `Service Temporarily Unavailable` 頁面。</li><li>當網站處於維護模式時， `var/` 目錄包含 `.maintenance.flag` 檔案。</li><li>您可以設定維護模式，允許訪客從指定的IP位址清單存取。</li></ul> |

>[!INFO]
>
>[Adobe Commerce雲基礎架構](https://devdocs.magento.com/cloud/bk-cloud.html) 僅支援生產和維護模式。

## 預設模式

如其名稱所示，若未指定其他模式，預設模式即為商務的運作方式。 預設模式可讓您在單一伺服器上部署商務應用程式，而不變更任何設定。 但是，預設模式沒有生產模式最佳化的模式。

要在多個伺服器上部署Commerce應用程式，或為生產而優化它，請更改為其他模式之一。

在預設模式中：

- 錯誤會記錄到伺服器的檔案報表，且從不向使用者顯示
- 快取靜態檢視檔案
- 預設模式未針對生產環境進行最佳化，主要是因為 [靜態檔案](https://glossary.magento.com/static-files) 動態產生，而非實體化。 換句話說，建立靜態檔案和快取對效能的影響比使用靜態檔案建立工具產生靜態檔案的影響要大。

請參閱 [設定操作模式](../cli/set-mode.md).

## 開發人員模式

擴充或自訂商務應用程式時，請以開發人員模式執行。

在開發人員模式中：

- 靜態檢視檔案不會進行快取；寫在 `pub/static` 每次呼叫目錄時
- 未捕獲的例外狀況會顯示在瀏覽器中
- 系統登錄 `var/report` 為verbose
- 安 [例外](https://glossary.magento.com/exception) 在錯誤處理常式中擲回，而非記錄
- 當 [事件](https://glossary.magento.com/event) 無法調用訂閱者

請參閱 [設定操作模式](../cli/set-mode.md).

## 生產模式

將商務部署到生產伺服器時，以生產模式運行它。 優化伺服器環境（如資料庫和Web伺服器）後，應運行 [靜態視圖檔案部署工具](../cli/static-view-file-deployment.md) 將靜態視圖檔案寫入 `pub/static` 目錄。

這可在部署時提供所有必要的靜態檔案，而不是強制商務在運行時按需動態查找和複製（實體化）靜態檔案，從而提高效能。

在生產模式中：

- 靜態視圖檔案不會實體化，且其URL會即時組成。 靜態檢視檔案由 [快取](https://glossary.magento.com/cache) 只有。
- 錯誤會記錄到檔案系統，且不會向使用者顯示。
- 您可以啟用和停用快取類型 _僅限_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- 您 _不能_ 使用「管理員」啟用或停用快取類型。

## 維護模式

在維護模式下運行商務應用程式，在您完成維護、升級或配置任務時使您的站點離線。 在維護模式中，網站會將訪客重新導向至預設 `Service Temporarily Unavailable` 頁面。

您可以建立 [自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md)、手動啟用和停用維護模式，以及設定維護模式，以允許來自授權IP位址的訪客正常檢視存放區。 請參閱 [啟用和禁用維護模式](../../installation/tutorials/maintenance-mode.md).

如果您在雲端基礎架構上使用Commerce，則Commerce應用程式會在部署階段以維護模式執行。 部署成功完成後，商務應用程式會返回到以生產模式執行。 請參閱 [部署掛接](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) 在 _Commerce Cloud指南_.
