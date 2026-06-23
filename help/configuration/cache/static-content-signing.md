---
title: 靜態內容簽署和瀏覽器快取失效
description: 瞭解靜態內容簽署如何在Adobe Commerce中運作，使靜態資源的瀏覽器快取失效。 瞭解如何啟用及設定此功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="僅適用於雲端上的Adobe Commerce和內部部署專案。"
autotag-review: '2026-06-22T21:48:08.334Z'
TQID: 'https://experienceleague.adobe.com/vagWBVnjIS7tjnwVE5Dk56VDmPtbPgjsNVLBHSlOc-s'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 372
ht-degree: 0%

---

# 靜態內容簽署和瀏覽器快取失效

為了改善效能，Commerce會為靜態資源（例如影像、JavaScript和CSS檔案）設定`Expires`標頭。
在靜態資源上設定`Expires`標頭，可告知瀏覽器在該URL快取資源並提供快取版本，直到它過期為止。
這是快取靜態資源的常見[最佳實務](https://developer.yahoo.com/performance/rules.html#expires=)。

當瀏覽器快取靜態資源，且該資源在伺服器上變更時，您必須清除瀏覽器快取，以便下載新版本。
如果您是網站管理員，手動清除瀏覽器快取可正常運作，但若您想要讓使用者下載靜態資源的新版本，則這不是適當的要求。

## 靜態內容簽署

靜態內容簽署是Commerce的一項功能，可讓您讓靜態資源的瀏覽器快取失效。
Commerce會將部署版本新增至靜態檔案的URL來達成此目的。

以下是以版本簽署的URL範例：

```text
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

當您執行命令[`setup:static-content:deploy`](../cli/static-view-file-deployment.md)以部署靜態內容時，Commerce會自動變更部署版本。
這會變更靜態檔案的URL，並強制瀏覽器載入檔案的新版本。

Commerce預設會啟用此功能，而Adobe建議啟用此功能，以防止瀏覽器提供舊靜態資源時出現問題。

靜態內容簽章的組態位於&#x200B;[**[!UICONTROL Stores]**>設定>組態>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures)。

- **僅限內部部署**：如果您的網站是[生產模式](../bootstrap/application-modes.md#production-mode)中的&#x200B;**非**，則可使用此設定。
- **雲端**：此設定已隱藏，因為生產模式是強制性的；因此，您必須使用命令列，如下所示。

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

判斷狀態：

```shell
bin/magento config:show dev/static/sign
```

啟用或停用靜態內容簽署：

```shell
bin/magento config:set dev/static/sign <value>
```

其中`<value>`為1 （已啟用）或0 （已停用）。

## 版本簽章

Commerce會將版本簽章直接在靜態檢視檔案的基礎URL後附加為路徑元件，以保留靜態資源間相對URL的完整性。
這也會強制瀏覽器將相對URL解析為正確的已簽署來源，同時保持其內容與簽章值的存在/不存在無關。

當瀏覽器向伺服器請求已簽署的來源時，伺服器會使用URL重寫來從URL中移除簽名元件。

## 部署期間的使用情況

升級或修改靜態資源後，您必須執行`setup:static-content:deploy`命令以部署版本並更新靜態內容，這會強制瀏覽器載入更新的資源。

如果您將程式碼部署在單獨的伺服器上，並使用程式碼存放庫將其移至生產環境以減少停機時間，您也必須將檔案`pub/static/deployed_version.txt`新增到存放庫。
此檔案包含已部署靜態內容的新版本。
