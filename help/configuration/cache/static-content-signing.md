---
title: 靜態內容快取
description: 了解靜態內容簽署，以及如何啟用或停用功能。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 靜態內容快取

為了改善效能，商務會設定 `Expires` 靜態資源（例如影像、JavaScript和CSS檔案）的標題。
設定 `Expires` 靜態資源的標題會告訴瀏覽器在該URL處快取資源，並提供快取版本，直到它過期為止。
這是常見的 [最佳實務](https://developer.yahoo.com/performance/rules.html#expires=) 用於快取靜態資源。

當瀏覽器快取靜態資源且該資源在伺服器上變更時，您必須清除瀏覽器快取，以便其下載新版本。
如果您是網站管理員，手動清除瀏覽器快取會有效，但當您想要使用者下載新版本的靜態資源時，這並不是對使用者提出的適當請求。

## 靜態內容簽名

靜態內容簽署是商務功能，可讓您使靜態資源的瀏覽器快取失效。
商務通過將部署版本添加到靜態檔案的URL來完成此操作。

以下是以版本簽署的URL範例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

運行命令時 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 要部署靜態內容，Commerce將自動更改部署版本。
這會變更靜態檔案的URL，並強制瀏覽器載入新版本的檔案。

商務預設會啟用此功能，而Adobe建議您持續啟用此功能，以防止發生與提供舊靜態資源的瀏覽器相關的問題。

您可以在 [**[!UICONTROL Stores]**>設定>設定>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

確定狀態：

```bash
bin/magento config:show dev/static/sign
```

啟用或禁用靜態內容簽名：

```bash
bin/magento config:set dev/static/sign <value>
```

其中 `<value>` 為1（已啟用）或0（已停用）。

## 版本簽名

商務會將版本簽章附加為路徑元件，直接在靜態檢視檔案的基本URL之後，以保留靜態資源中相對URL的完整性。
這也會強制瀏覽器解析指向正確簽名源的相對URL，同時使其內容與簽名值的存在/不存在無關。

當瀏覽器向伺服器請求已簽名的源時，伺服器會使用URL重寫來從URL中刪除簽名元件。

## 部署期間的使用情況

升級或修改靜態資源後，您必須執行 `setup:static-content:deploy` 命令來部署版本和更新靜態內容，這會強制瀏覽器載入更新的資源。

如果您將程式碼部署在個別伺服器上，並使用程式碼存放庫將程式碼移至生產環境，以減少停機時間，您也必須新增檔案 `pub/static/deployed_version.txt` 至存放庫。
此檔案包含已部署靜態內容的新版本。
