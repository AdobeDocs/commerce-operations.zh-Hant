---
title: 配置鎖定提供程式
description: 請依照下列步驟，防止重複cron工作和cron群組在您的Adobe Commerce或Magento Open Source部署上執行。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# 配置鎖定提供程式

在運行此命令之前，您必須執行以下操作 *或* 您必須 [安裝應用程式](../advanced.md):

* [建立或更新部署配置](deployment.md)
* [建立資料庫架構](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 配置鎖

設定鎖定提供者以防止啟動重複cron作業和cron群組。 (需要Adobe Commerce或Magento Open Source2.2.x、2.2.5和更新版本，以及2.3.3和更新版本。)

Adobe Commerce和Magento Open Source預設會使用資料庫儲存鎖。 如果您的伺服器上有多個節點，建議您使用Zookeeper作為鎖定提供者。

如果您在雲端基礎架構上執行Adobe Commerce，則不需要配置鎖定提供程式設定。 應用程式在配置過程中為Pro項目配置檔案鎖定提供程式。 請參閱 [雲端變數](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### 命令用法

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 參數說明

| 名稱 | 值 | 必要？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供程式名稱： `db`, `zookeeper`，或 `file`.<br><br>預設鎖定提供程式： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫前置詞 `db` 鎖定提供程式。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用時連接到Zookeeper群集的主機和埠 `zookeeper` 鎖定提供程式。<br><br>例如： `127.0.0.1:2181` | 是，若您設定 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存鎖的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 保存檔案鎖的路徑。 | 是，若您設定 `--lock-provider=file` |
