---
title: 移轉變更
description: 瞭解如何僅移轉自您上次使用 [!DNL Data Migration Tool]移轉Magento1資料以來變更的資料。
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# 移轉變更

增量移轉工具會在[資料移轉](data.md)期間，在Magento1資料庫中安裝deltalog表格（首碼為`m2_cl_*`）和觸發器（用於追蹤變更）。 若要確保僅移轉自上次移轉資料以來在Magento1中所做的變更，這些刪除表格和觸發程式至關重要。 這些變更包括：

* 客戶透過店面新增的資料（已建立的訂單、評論和客戶設定檔中的變更）

* 「管理員」面板中訂單、產品和類別的所有作業

>[!NOTE]
>
>所有其他透過管理員輸入的新實體或更新實體（例如屬性或CMS頁面）不會納入增量移轉中，也不會移轉。


開始之前，請採取下列步驟進行準備：

1. 以[檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md)的身份登入應用程式伺服器。
1. 變更至`/bin`目錄，或確認已將其新增至您的系統`PATH`。

如需詳細資訊，請參閱[第一個步驟](overview.md#first-steps)區段。

## 執行增量移轉命令

若要開始移轉增量變更，請執行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]`是從頭開始移轉的可選引數。 您可以使用此引數來測試移轉。

* `[-a|--auto]`是選擇性引數，可防止移轉在遇到完整性檢查錯誤時停止。

* `{<path to config.xml>}`是`config.xml`的絕對檔案系統路徑；此引數為必要項。

>[!NOTE]
>
>增量移轉是一個持續的過程；每5秒會自動重新啟動。 使用CTRL-C中止移轉程式。


## 移轉由協力廠商擴充功能建立的資料

在`Delta`模式中，[!DNL Data Migration Tool]會移轉僅由Magento自己的模組所建立的資料，且不負責協力廠商開發人員所編寫的程式碼或擴充功能。 如果這些擴充功能在店面資料庫中建立了資料，且商家想要在Magento2中擁有這些資料，則應建立並相應修改[!DNL Data Migration Tool]的設定檔。

如果擴充功能有自己的表格，而您需要追蹤其變更以進行差異移轉，請遵循下列步驟：

1. 將要追蹤的資料表新增至`deltalog.xml`檔案
1. 建立擴充`Migration\App\Step\AbstractDelta`的額外差異類別
1. 將新建立的類別名稱新增至`config.xml`的差異模式區段
