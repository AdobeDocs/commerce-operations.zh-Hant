---
title: 應用模式
description: Commerce應用程式可以根據您的需要以不同的模式運行。 查看可用應用程式模式的詳細清單。
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# 應用模式

您可以在以下任一操作中運行Commerce應用程式 _模式_:

| 模式名稱 | 說明 | 雲支援 |
| ------------------------ | ------------------- | ------------- |
| [預設](#default-mode) | 在單台伺服器上部署和運行Commerce應用程式，而不更改設定。 _不是_ 已針對生產進行優化。 | 不 |
| [開發者](#developer-mode) | 在擴展或定制Commerce應用程式時是開發的理想選擇。 | 不 |
| [生產](#production-mode) | 將Commerce應用程式部署到生產系統並運行。 | 是 |
| [維護](#maintenance-mode) | 在執行更新和配置時防止訪問站點。 | 是 |

請參閱 [設定操作模式](../cli/set-mode.md) 瞭解如何手動更改Adobe Commerce操作模式。

## 雲支援

無需管理雲基礎架構項目的應用程式模式。 由於是只讀檔案系統，您無法更改遠程雲環境中的模式。 Adobe Commerce在雲基礎架構上自動運行應用程式 _維護_ 模式，使您的站點離線，直到部署完成。 否則，應用程式將保留在 _生產_ 的子菜單。 請參閱 [部署過程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) 的 _雲基礎架構上的商務指南_。

如果您將Cloud Docker for Commerce用作開發工具，則可以在Docker環境中部署您的雲基礎架構項目 _開發者_ 模式，但由於其他檔案同步操作，效能較慢。 請參閱 [部署Docker環境](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) 的 _Cloud Docker for Commerce指南_。

## 預設模式

的 _預設_ 模式使您可以在單台伺服器上部署Commerce應用程式，而不更改任何設定。 但是，由於靜態檔案對效能的不利影響，預設模式未針對生產進行優化。 建立靜態檔案並快取它們比使用靜態檔案建立工具生成它們具有更大的效能影響。

在預設模式下：

- 異常將寫入日誌檔案而不是顯示
- 靜態視圖檔案已快取
- 隱藏自定義 `X-Magento-*` HTTP請求和響應標頭

如果未指定其他模式，則Commerce在預設模式下運行。

## 開發人員模式

的 _開發者_ 建議使用模式來擴展和自定義Commerce應用程式。 靜態視圖檔案未快取，但已寫入 `pub/static` 目錄。

在開發人員模式下：

- 啟用 [自動代碼編譯](../cli/code-compiler.md) 增強調試
- 未捕獲的異常顯示在瀏覽器中
- 系統登錄 `var/report` 詳細
- 錯誤處理程式中引發異常，而不是記錄
- 無法調用事件訂閱伺服器時引發異常
- 顯示自定義 `X-Magento-*` HTTP請求和響應標頭

## 生產模式

的 _生產_ 模式最適合在生產系統上部署Commerce應用程式。 優化伺服器環境（如資料庫和Web伺服器）後，應運行 [靜態視圖檔案部署工具](../cli/static-view-file-deployment.md) 將靜態視圖檔案寫入 `pub/static` 的子菜單。 這通過在部署時提供所有必要的靜態檔案而不是強制Commerce應用程式在運行期間按需動態查找和複製（實體化）靜態檔案而提高了效能。

某些欄位（如管理中的「高級」和「開發人員」系統配置部分）在生產模式下不可用。 比如說你 _不能_ 使用Admin啟用或禁用快取類型。 可以啟用和禁用快取類型 _僅_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en)。

在生產模式中：

- 靜態視圖檔案僅從快取提供
- 錯誤和異常記錄到檔案系統中，並且永遠不會顯示給用戶
- 管理員中的某些配置欄位不可用

## 維護模式

的 _維護_ 模式限制或禁止在改進、更新和配置任務期間訪問站點。 預設情況下，站點將訪問者重定向到預設 `Service Temporarily Unavailable` 的子菜單。

可以建立 [自定義維護頁](../../upgrade/troubleshooting/maintenance-mode-options.md)，手動啟用和禁用維護模式，並配置維護模式，以允許來自授權IP地址的訪問者正常查看儲存。 請參閱 [啟用和禁用維護模式](../../installation/tutorials/maintenance-mode.md) 的 _安裝指南_。

如果您在雲基礎架構上使用Commerce，則Commerce應用程式在部署階段以維護模式運行。 部署成功完成後，Commerce應用程式將返回到在生產模式下運行。 請參閱 [部署掛接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 的 _雲基礎架構上的商務指南_。

在維護模式下：

- 站點訪問者被重定向到預設 `Service Temporarily Unavailable` 頁
- 的 `var/` 目錄包含 `.maintenance.flag` 檔案
- 您可以根據IP地址限制訪問者訪問
