---
title: 靜態內容快取
description: 瞭解靜態內容簽署以及如何啟用或停用此功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: d099d60bcf3c960b2e40b48c386041d8865cfb50
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 靜態內容快取

為改善效能，Commerce將 `Expires` 靜態資源的標頭，例如影像、JavaScript和CSS檔案。
設定 `Expires` 靜態資源上的標頭會告訴瀏覽器在該URL快取資源並提供快取版本，直到它過期為止。
這是常見的 [最佳實務](https://developer.yahoo.com/performance/rules.html#expires=) 用於快取靜態資源。

當瀏覽器快取靜態資源，且該資源在伺服器上變更時，您必須清除瀏覽器快取，以便下載新版本。
如果您是網站管理員，手動清除瀏覽器快取可正常運作，但若您想要讓使用者下載靜態資源的新版本，則這不是適當的要求。

## 靜態內容簽署

靜態內容簽署是Commerce功能，可讓您讓靜態資源的瀏覽器快取失效。
Commerce會將部署版本新增至靜態檔案的URL來達成此目的。

以下是以版本簽署的URL範例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

當您執行指令時 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 若要部署靜態內容，Commerce會自動變更部署版本。
這會變更靜態檔案的URL，並強制瀏覽器載入檔案的新版本。

根據預設，Commerce會啟用此功能，Adobe建議啟用此功能，以防止瀏覽器提供舊靜態資源時出現問題。

靜態內容簽章的設定已存取 [**[!UICONTROL Stores]**>設定>設定>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

- **僅限內部部署**：如果您的網站為 **非** 在 [生產模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode).
- **雲端**：此設定為隱藏，因為生產模式是強制性的；因此，您必須使用命令列，如下所示。

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

判斷狀態：

```bash
bin/magento config:show dev/static/sign
```

啟用或停用靜態內容簽署：

```bash
bin/magento config:set dev/static/sign <value>
```

位置 `<value>` 為1 （已啟用）或0 （已停用）。

## 版本簽章

Commerce會將版本簽章直接附加為靜態檢視檔案的基礎URL之後的路徑元件，以保留靜態資源間相對URL的完整性。
這也會強制瀏覽器將相對URL解析為正確的已簽署來源，同時保持其內容與簽章值的存在/不存在無關。

當瀏覽器向伺服器請求已簽署的來源時，伺服器會使用URL重寫來從URL中移除簽名元件。

## 部署期間的使用情況

升級或修改靜態資源後，您必須執行 `setup:static-content:deploy` 用於部署版本和更新靜態內容的命令，會強制瀏覽器載入更新的資源。

如果您將程式碼部署在單獨的伺服器上，並使用程式碼存放庫將其移至生產環境以減少停機時間，您也必須新增檔案 `pub/static/deployed_version.txt` 至存放庫。
此檔案包含已部署靜態內容的新版本。
