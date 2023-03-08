---
title: 應用程式模式
description: 根據您的需求，商務應用程式可以以不同模式運作。 查看可用應用程式模式的詳細清單。
source-git-commit: e7c325aef90d4135218b984cc57df2c8d1d921d2
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---


# 應用程式模式

您可以在下列任一項中執行商務應用程式 _模式_:

| 模式名稱 | 說明 | 雲端支援 |
| ------------------------ | ------------------- | ------------- |
| [預設](#default-mode) | 在單一伺服器上部署和運行Commerce應用程式，而不更改設定。 _Not_ 針對生產環境進行最佳化。 | no |
| [開發人員](#developer-mode) | 非常適合用於擴充或自訂商務應用程式的開發。 | no |
| [生產](#production-mode) | 將商務應用程式部署並運行到生產系統。 | 是 |
| [維護](#maintenance-mode) | 在執行更新和設定時防止存取網站。 | 是 |

請參閱 [設定操作模式](../cli/set-mode.md) 了解如何手動變更Adobe Commerce操作模式。

## 雲端支援

無需管理雲基礎架構項目的應用程式模式。 由於是只讀檔案系統，因此您無法更改遠程雲環境中的模式。 雲端基礎架構上的Adobe Commerce會自動執行 _維護_ 模式，這會讓您的網站離線，直到部署完成為止。 否則，應用程式會保留在 _生產_ 模式。 請參閱 [部署過程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) 在 _雲端基礎架構商務指南_.

如果您使用Cloud Docker for Commerce作為開發工具，則可在 _開發人員_ 模式，但由於其他檔案同步操作，效能較慢。 請參閱 [部署Docker環境](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) 在 _Cloud Docker for Commerce指南_.

## 預設模式

此 _預設_ 模式可讓您在單一伺服器上部署商務應用程式，而不變更任何設定。 但是，由於靜態檔案對效能的不利影響，預設模式沒有針對生產進行最佳化。 建立靜態檔案和快取對效能的影響比使用靜態檔案建立工具生成靜態檔案要大。

在預設模式中：

- 例外情況會寫入記錄檔而非顯示
- 快取靜態檢視檔案
- 隱藏自訂 `X-Magento-*` HTTP要求和回應標題

如果未指定其他模式，則商務會以預設模式運行。

## 開發人員模式

此 _開發人員_ 建議使用模式來擴充和自訂商務應用程式。 靜態檢視檔案不會進行快取，但會寫入 `pub/static` 目錄。

在開發人員模式中：

- 啟用 [自動代碼編譯](../cli/code-compiler.md) 及增強除錯功能
- 未捕獲的例外狀況會顯示在瀏覽器中
- 系統登錄 `var/report` 為verbose
- 錯誤處理常式中擲回例外狀況，而非記錄
- 無法調用事件訂閱伺服器時，會引發異常
- 顯示自訂 `X-Magento-*` HTTP要求和回應標題

## 生產模式

此 _生產_ 模式最適合在生產系統上部署商務應用程式。 優化伺服器環境（如資料庫和Web伺服器）後，應運行 [靜態視圖檔案部署工具](../cli/static-view-file-deployment.md) 將靜態視圖檔案寫入 `pub/static` 目錄。 這可在部署時提供所有必要的靜態檔案，而不是強制Commerce應用程式在運行時按需動態查找和複製（實體化）靜態檔案，從而提高效能。

有些欄位（例如「管理員」中的「進階」和「開發人員」系統設定區段）在生產模式中無法使用。 例如，您 _不能_ 使用「管理員」啟用或停用快取類型。 您可以啟用和停用快取類型 _僅限_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en).

在生產模式中：

- 靜態檢視檔案僅從快取提供
- 錯誤和例外記錄到檔案系統，且從不向用戶顯示
- 「管理」中的某些設定欄位無法使用

## 維護模式

此 _維護_ 模式會在改善、更新和設定工作期間限制或防止存取網站。 依預設，網站會將訪客重新導向至預設 `Service Temporarily Unavailable` 頁面。

您可以建立 [自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md)、手動啟用和停用維護模式，以及設定維護模式，以允許來自授權IP位址的訪客正常檢視存放區。 請參閱 [啟用和禁用維護模式](../../installation/tutorials/maintenance-mode.md) 在 _安裝指南_.

如果您在雲端基礎架構上使用Commerce，則Commerce應用程式會在部署階段以維護模式執行。 部署成功完成後，商務應用程式會返回到以生產模式執行。 請參閱 [部署掛接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 在 _雲端基礎架構商務指南_.

在維護模式中：

- 系統會將網站訪客重新導向至預設 `Service Temporarily Unavailable` 頁面
- 此 `var/` 目錄包含 `.maintenance.flag` 檔案
- 您可以根據IP位址限制訪客存取
