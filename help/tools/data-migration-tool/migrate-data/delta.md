---
title: 遷移更改
description: 瞭解如何僅遷移自上次Magento1資料遷移後更改的資料， [!DNL Data Migration Tool]。
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# 遷移更改

增量遷移工具安裝deltalog表（帶前置詞） `m2_cl_*`)和觸發器(用於跟蹤Magento1資料庫中的更改) [資料遷移](data.md)。 這些Deltalog表和觸發器對於確保僅遷移自上次遷移資料以來在Magento1中所做的更改至關重要。 這些更改包括：

* 客戶通過 [店面](https://glossary.magento.com/storefront) （已建立訂單、審閱和客戶配置檔案的更改）

* 所有具有訂單、產品和類別的操作 [管理](https://glossary.magento.com/magento-admin) 面板

>[!NOTE]
>
>通過管理員輸入的所有其他新實體或更新的實體（如屬性或CMS頁）均不包括在增量遷移中，也不會遷移。


在開始之前，請執行以下步驟準備：

1. 登錄到Magento伺服器時 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
1. 更改為Magento `/bin` 目錄或確保它已添加到系統PATH中。

查看 [第一步](overview.md#first-steps) 的子菜單。

## 運行增量遷移命令

要開始遷移增量更改，請運行：

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

位置：

* `[-r|--reset]` 是從頭開始遷移的可選參數。 您可以使用此參數來測試遷移。

* `[-a|--auto]` 是一個可選參數，可防止在遇到完整性檢查錯誤時停止遷移。

* `{<path to config.xml>}` 是到 `config.xml`;此參數是必需的。

>[!NOTE]
>
>增量遷移是一個連續的過程；它每5秒自動重啟一次。 使用CTRL-C中止遷移過程。


## 遷移由第三方擴展建立的資料

在 `Delta` 的 [!DNL Data Migration Tool] 遷移僅由Magento自己的模組建立的資料，不負責第三方開發人員的代碼或擴展。 如果這些擴展在儲存前資料庫中建立了資料，並且商戶希望將此資料放在Magento2中， [!DNL Data Migration Tool] 應建立並相應修改。

如果 [擴展](https://glossary.magento.com/extension) 有自己的表，您需要跟蹤它們對增量遷移的更改，請執行以下步驟：

1. 將要跟蹤的表添加到 `deltalog.xml` 檔案
1. 建立擴展 `Migration\App\Step\AbstractDelta`
1. 將新建立的類的名稱添加到的增量模式部分 `config.xml`
