---
title: 應用程式模式
description: Commerce應用程式可依您的需求以不同模式運作。 檢視可用的應用程式模式詳細清單。
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 5003e8dcbb3736201ea19ebe30d5e56775096157
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# 應用程式模式

您可以在下列任一&#x200B;_模式_&#x200B;中執行Commerce應用程式：

| 模式名稱 | 說明 | 雲端支援 |
| ------------------------ | ------------------- | ------------- |
| [預設](#default-mode) | 在單一伺服器上部署及執行Commerce應用程式，而不變更設定。 _不_&#x200B;已針對生產最佳化。 | 否 |
| [開發人員](#developer-mode) | 適用於擴充或自訂Commerce應用程式時的開發。 | 否 |
| [生產](#production-mode) | 將Commerce應用程式部署並執行至生產系統。 | 是 |
| [維護](#maintenance-mode) | 執行更新和設定時防止存取網站。 | 是 |

請參閱[設定操作模式](../cli/set-mode.md)以瞭解如何手動變更Adobe Commerce操作模式。

## 雲端支援

因為唯讀檔案系統，您無法變更遠端雲端環境中的模式。 請勿嘗試透過修改`app/etc/env.php`檔案來變更模式，因為`ece-tools`封裝會根據多個組態來源覆寫檔案。

雲端基礎結構上的Adobe Commerce會在部署期間以&#x200B;_維護_&#x200B;模式自動執行應用程式，讓您的網站離線，直到部署完成。 否則，應用程式會維持在&#x200B;_生產_&#x200B;模式。 請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[部署程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase)。

如果您使用Commerce的Cloud Docker作為開發工具，則可以在&#x200B;_開發人員_&#x200B;模式的Docker環境中部署雲端基礎結構專案，但由於額外的檔案同步處理作業，效能會變慢。 請參閱&#x200B;_適用於Commerce的Cloud Docker指南_&#x200B;中的[部署Docker環境](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode)。

## 預設模式

_預設_&#x200B;模式可讓您在單一伺服器上部署Commerce應用程式，而不變更任何設定。 不過，由於靜態檔案對效能的不利影響，預設模式不會針對生產進行最佳化。 建立靜態檔案並快取這些檔案比使用靜態檔案建立工具產生這些檔案對效能的影響更大。

在預設模式中：

- 例外狀況會寫入記錄檔而非顯示
- 靜態檢視檔案已快取
- 隱藏自訂`X-Magento-*` HTTP要求與回應標頭

若未指定其他模式，Commerce會以預設模式運作。

## 開發人員模式

建議使用&#x200B;_開發人員_&#x200B;模式來擴充及自訂Commerce應用程式。 未快取靜態檢視檔案，但會視需要寫入`pub/static`目錄。

在開發人員模式中：

- 啟用[自動程式碼編譯](../cli/code-compiler.md)和增強型偵錯
- 瀏覽器中會顯示未攔截到的例外狀況
- `var/report`中的系統記錄為詳細資訊
- 錯誤處理常式中會擲回例外狀況，而非加以記錄
- 無法叫用事件訂閱者時，會擲回例外狀況
- 顯示自訂`X-Magento-*` HTTP要求與回應標頭

## 生產模式

_生產_&#x200B;模式最適合在生產系統上部署Commerce應用程式。 在最佳化伺服器環境（例如資料庫和網頁伺服器）之後，您應該執行[靜態檢視檔案部署工具](../cli/static-view-file-deployment.md)，將靜態檢視檔案寫入`pub/static`目錄。 這可透過在部署時提供所有必要的靜態檔案來改善效能，而不是強制Commerce應用程式在執行階段期間依需求動態尋找和複製（具體化）靜態檔案。

某些欄位，例如管理員中的進階和開發人員系統設定區段，在生產模式中無法使用。 例如，您&#x200B;_無法_&#x200B;使用Admin啟用或停用快取型別。 您可以使用[命令列](../cli/manage-cache.md#config-cli-subcommands-cache-en)來啟用和停用快取型別&#x200B;_僅限_。

在生產模式中：

- 靜態檢視檔案僅由快取提供
- 錯誤和例外會記錄到檔案系統，且永遠不會顯示給使用者
- 管理員中的某些設定欄位無法使用

## 維護模式

_維護_&#x200B;模式會在改善、更新及設定工作期間，限制或防止存取網站。 依預設，網站會將訪客重新導向預設`Service Temporarily Unavailable`頁面。

您可以建立[自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md)、手動啟用和停用維護模式，以及設定維護模式，以允許來自授權IP位址的訪客正常檢視存放區。 請參閱&#x200B;_安裝指南_&#x200B;中的[啟用和停用維護模式](../../installation/tutorials/maintenance-mode.md)。

如果您在雲端基礎結構上使用Commerce，Commerce應用程式會在部署階段以維護模式執行。 部署成功完成時，Commerce應用程式會回到生產模式中執行。 請參閱&#x200B;_雲端基礎結構上的Commerce指南_&#x200B;中的[部署勾點](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks)。

在維護模式中：

- 網站訪客被重新導向至預設`Service Temporarily Unavailable`頁面
- `var/`目錄包含`.maintenance.flag`檔案
- 您可以根據IP位址限制訪客存取
