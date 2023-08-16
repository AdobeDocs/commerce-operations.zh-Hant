---
title: 應用程式模式
description: Commerce應用程式可依您的需求以不同模式運作。 檢視可用的應用程式模式詳細清單。
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# 應用程式模式

您可以在下列任一項中執行商務應用程式 _模式_：

| 模式名稱 | 說明 | 雲端支援 |
| ------------------------ | ------------------- | ------------- |
| [預設](#default-mode) | 在單一伺服器上部署及執行Commerce應用程式，而不變更設定。 _Not_ 針對生產最佳化。 | 否 |
| [開發人員](#developer-mode) | 適用於擴充或自訂商務應用程式時的開發。 | 否 |
| [生產](#production-mode) | 將商務應用程式部署並執行至生產系統。 | 是 |
| [維護作業](#maintenance-mode) | 執行更新和設定時防止存取網站。 | 是 |

另請參閱 [設定作業模式](../cli/set-mode.md) 以瞭解如何手動變更Adobe Commerce操作模式。

## 雲端支援

不需要管理雲端基礎結構專案的應用程式模式。 因為唯讀檔案系統，您無法變更遠端雲端環境中的模式。 雲端基礎結構上的Adobe Commerce會自動在中執行應用程式 _維護作業_ 模式，可讓您的網站離線，直到部署完成。 否則，應用程式會保留在 _生產_ 模式。 另請參閱 [部署流程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) 在 _雲端基礎結構上的Commerce指南_.

如果您使用Cloud Docker for Commerce作為開發工具，您可以在以下位置在Docker環境中部署雲端基礎結構專案 _開發人員_ 模式，但因為額外的檔案同步作業而造成效能變慢。 另請參閱 [部署Docker環境](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) 在 _Cloud Docker for Commerce指南_.

## 預設模式

此 _預設_ 模式可讓您在單一伺服器上部署Commerce應用程式，而不變更任何設定。 不過，由於靜態檔案對效能的不利影響，預設模式不會針對生產進行最佳化。 建立靜態檔案並快取這些檔案比使用靜態檔案建立工具產生這些檔案對效能的影響更大。

在預設模式中：

- 例外狀況會寫入記錄檔而非顯示
- 靜態檢視檔案已快取
- 隱藏自訂 `X-Magento-*` HTTP要求與回應標頭

如果未指定其他模式，Commerce會在預設模式下運作。

## 開發人員模式

此 _開發人員_ 建議使用模式來擴充及自訂商務應用程式。 靜態檢視檔案不會快取，但會寫入 `pub/static` 隨選目錄。

在開發人員模式中：

- 啟用 [自動程式碼編譯](../cli/code-compiler.md) 和增強型除錯
- 瀏覽器中會顯示未攔截到的例外狀況
- 系統登入 `var/report` 冗長
- 錯誤處理常式中會擲回例外狀況，而非加以記錄
- 無法叫用事件訂閱者時，會擲回例外狀況
- 顯示自訂 `X-Magento-*` HTTP要求與回應標頭

## 生產模式

此 _生產_ 模式最適合在生產系統上部署Commerce應用程式。 最佳化伺服器環境（例如資料庫和網頁伺服器）之後，您應該執行 [靜態檢視檔案部署工具](../cli/static-view-file-deployment.md) 將靜態檢視檔案寫入 `pub/static` 目錄。 這可透過在部署時提供所有必要的靜態檔案來改善效能，而不是強制商務應用程式在執行階段期間依需求動態尋找和複製（具體化）靜態檔案。

某些欄位，例如管理員中的進階和開發人員系統設定區段，在生產模式中無法使用。 例如，您 _無法_ 使用Admin啟用或停用快取型別。 您可以啟用和停用快取型別 _僅限_ 使用 [命令列](../cli/manage-cache.md#config-cli-subcommands-cache-en).

在生產模式中：

- 靜態檢視檔案僅由快取提供
- 錯誤和例外會記錄到檔案系統，且永遠不會顯示給使用者
- 管理員中的某些設定欄位無法使用

## 維護模式

此 _維護作業_ 在改善、更新及設定工作時，模式會限制或防止存取網站。 依預設，網站會將訪客重新導向至預設值 `Service Temporarily Unavailable` 頁面。

您可以建立 [自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md)，手動啟用和停用維護模式，並設定維護模式以允許來自授權IP位址的訪客正常檢視存放區。 另請參閱 [啟用和停用維護模式](../../installation/tutorials/maintenance-mode.md) 在 _安裝指南_.

如果您在雲端基礎結構上使用Commerce，Commerce應用程式會在部署階段以維護模式執行。 部署成功完成時，商務應用程式會返回以生產模式執行。 另請參閱 [部署勾點](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 在 _雲端基礎結構上的Commerce指南_.

在維護模式中：

- 網站訪客會重新導向至預設值 `Service Temporarily Unavailable` 頁面
- 此 `var/` 目錄包含 `.maintenance.flag` 檔案
- 您可以根據IP位址限制訪客存取
