---
title: 配置鎖提供程式
description: 請執行以下步驟，防止在您的Adobe Commerce或Magento Open Source部署上運行重複的cron作業和cron組。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 配置鎖提供程式

在運行此命令之前，必須執行以下操作 *或* 必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 配置鎖

配置鎖提供程式以阻止啟動重複的cron作業和cron組。 (需要Adobe Commerce或Magento Open Source2.2.x、2.2.5和更高版本以及2.3.3和更高版本。)

Adobe Commerce和Magento Open Source使用資料庫在預設情況下保存鎖。 如果您的伺服器上有多個節點，我們建議使用Zookeeper作為鎖提供程式。

如果您在雲基礎架構上運行Adobe Commerce，則無需配置鎖提供程式設定。 應用程式在預配過程中為Pro項目配置檔案鎖定提供程式。 請參閱 [雲變數](https://devdocs.magento.com/cloud/env/variables-cloud.html)。

### 命令用法

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 參數說明

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供程式名稱： `db`。 `zookeeper`或 `file`。<br><br>預設鎖提供程式： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫前置詞 `db` 鎖定提供程式。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用 `zookeeper` 鎖定提供程式。<br><br>例如： `127.0.0.1:2181` | 是的，如果 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存鎖的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 保存檔案鎖的路徑。 | 是的，如果 `--lock-provider=file` |
