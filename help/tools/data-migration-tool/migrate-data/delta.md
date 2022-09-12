---
title: 移轉變更
description: 了解如何僅移轉自上次Magento1資料移轉後已變更的資料，透過 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# 移轉變更

增量遷移工具安裝增量表（帶前置詞） `m2_cl_*`)和觸發器(用於追蹤Magento1資料庫中的變更) [資料移轉](data.md). 這些委派表和觸發器對於確保您僅移轉自上次移轉資料以來，Magento1中所做的變更至關重要。 這些變更包括：

* 客戶透過 [店面](https://glossary.magento.com/storefront) （在客戶設定檔中建立訂單、審核和變更）

* 所有操作都包含訂單、產品和類別 [管理](https://glossary.magento.com/magento-admin) 面板

>[!NOTE]
>
>透過管理員輸入的所有其他新實體或更新實體（例如屬性或CMS頁面）均不包含在增量移轉中，也不會移轉。


開始之前，請執行下列步驟以準備：

1. 登錄到應用程式伺服器，作為 [檔案系統所有者](../../../installation/prerequisites/file-system/overview.md).
1. 變更為 `/bin` 目錄，或確認已將其新增至您的系統 `PATH`.

請參閱 [第一步](overview.md#first-steps) 一節以取得詳細資訊。

## 運行增量遷移命令

要開始遷移增量更改，請運行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是從頭開始移轉的選用引數。 您可以使用此引數來測試移轉。

* `[-a|--auto]` 是可選引數，當遇到完整性檢查錯誤時，該引數會阻止遷移停止。

* `{<path to config.xml>}` 是的絕對檔案系統路徑 `config.xml`;此引數為必要項目。

>[!NOTE]
>
>增量遷移是一個連續的過程；每5秒自動重新啟動一次。 使用CTRL-C中止移轉程式。


## 移轉由協力廠商擴充功能建立的資料

在 `Delta` 模式， [!DNL Data Migration Tool] 移轉僅由Magento自己的模組建立的資料，且不負責協力廠商開發人員所製作的程式碼或擴充功能。 如果這些擴展在店面資料庫中建立了資料，並且商家希望在Magento2中包含此資料，即 [!DNL Data Migration Tool] 應據此建立和修改。

若 [擴充功能](https://glossary.magento.com/extension) 有自己的表，並且您需要跟蹤它們對delta遷移的更改，請執行以下步驟：

1. 將要追蹤的表格新增至 `deltalog.xml` 檔案
1. 建立其他增量類，以擴展 `Migration\App\Step\AbstractDelta`
1. 將新建立類的名稱添加到的增量模式部分 `config.xml`
