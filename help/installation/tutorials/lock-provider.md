---
title: 設定鎖定提供者
description: 請依照下列步驟，防止重複的cron工作和cron群組在您的Adobe Commerce部署中執行。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 設定鎖定提供者

執行此指令之前，您必須執行下列動作 *或* 您必須 [安裝應用程式](../advanced.md)：

* [建立或更新部署設定](deployment.md)
* [建立資料庫綱要](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 設定鎖定

設定鎖定提供者，以防止啟動重複的cron作業和cron群組。 (需要Adobe Commerce 2.2.x、2.2.5和更新版本，以及2.3.3和更新版本。)

Adobe Commerce預設會使用資料庫儲存鎖定。 如果您的伺服器上有多個節點，建議您使用Zookeeper做為鎖定提供者。

如果您在雲端基礎結構上執行Adobe Commerce，則不需要設定鎖定提供者設定。 應用程式會在布建程式期間為Pro專案設定檔案鎖定提供者。 另請參閱 [雲端變數](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### 命令使用方式

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 引數說明

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供者名稱： `db`， `zookeeper`，或 `file`.<br><br>預設鎖定提供者： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫首碼 `db` 鎖定提供者。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用Zookeeper叢集時連線至該叢集的主機與連線埠 `zookeeper` 鎖定提供者。<br><br>例如： `127.0.0.1:2181` | 是，如果您設定 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper儲存鎖定的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 儲存檔案鎖定的路徑。 | 是，如果您設定 `--lock-provider=file` |
