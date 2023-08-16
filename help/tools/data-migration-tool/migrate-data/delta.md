---
title: 移轉變更
description: 瞭解如何僅移轉自您上次Magento1資料移轉以來有所變更的資料，使用 [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# 移轉變更

增量移轉工具會安裝增量表格（前置詞） `m2_cl_*`)和觸發器（用於追蹤變更）的數量，以及Magento1資料庫中的 [資料移轉](data.md). 若要確保僅移轉自上次移轉資料以來在Magento1中所做的變更，這些刪除表格和觸發程式至關重要。 這些變更包括：

* 客戶透過店面新增的資料（已建立的訂單、評論和客戶設定檔中的變更）

* 「管理員」面板中訂單、產品和類別的所有作業

>[!NOTE]
>
>所有其他透過管理員輸入的新實體或更新實體（例如屬性或CMS頁面）不會納入增量移轉中，也不會移轉。


開始之前，請採取下列步驟進行準備：

1. 以下列身分登入應用程式伺服器： [檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md).
1. 變更為 `/bin` 目錄，或確認已將其新增至您的系統 `PATH`.

請參閱 [第一步](overview.md#first-steps) 區段以取得更多詳細資料。

## 執行增量移轉命令

若要開始移轉增量變更，請執行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是選用引數，會從頭開始移轉。 您可以使用此引數來測試移轉。

* `[-a|--auto]` 是選用引數，可防止移轉在遇到完整性檢查錯誤時停止。

* `{<path to config.xml>}` 是絕對檔案系統路徑 `config.xml`；此引數為必要專案。

>[!NOTE]
>
>增量移轉是一個持續的過程；每5秒會自動重新啟動。 使用CTRL-C中止移轉程式。


## 移轉由協力廠商擴充功能建立的資料

在 `Delta` 模式， [!DNL Data Migration Tool] 會移轉僅由Magento本身模組建立的資料，對協力廠商開發人員提供的程式碼或擴充功能概不負責。 如果這些擴充功能在店面資料庫中建立了資料，且商家想要在Magento2中擁有這些資料 — 的設定檔 [!DNL Data Migration Tool] 應據以建立及修改。

如果擴充功能有自己的表格，而您需要追蹤其變更以進行差異移轉，請遵循下列步驟：

1. 將要追蹤的表格新增至 `deltalog.xml` 檔案
1. 建立額外的delta類別，以擴充 `Migration\App\Step\AbstractDelta`
1. 將新建立的類別名稱新增到的差異模式區段 `config.xml`
