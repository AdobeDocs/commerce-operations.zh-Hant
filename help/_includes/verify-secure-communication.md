---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 驗證通信是否安全

本節探討兩種驗證HTTP基本驗證是否正常運作的方法：

* 使用 `curl` 用於驗證的命令必須輸入用戶名和密碼才能獲取群集狀態
* 在管理員中設定HTTP基本驗證

## 使用 `curl` 驗證群集狀態的命令

輸入以下命令：

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如，如果在搜索引擎伺服器上輸入命令，而代理使用埠8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

將顯示以下消息以指示身份驗證失敗：

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

現在，嘗試以下命令：

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如：

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

這次，命令會以類似下列的訊息成功：

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 在管理員中設定HTTP Basic驗證

執行與 [搜尋引擎設定](../configuration/search/configure-search-engine.md) *expert* 按一下 **[!UICONTROL Yes]** 從 **[!UICONTROL Enable Elasticsearch HTTP Auth]** 列出並在提供的欄位中輸入您的使用者名稱和密碼。

按一下 **[!UICONTROL Test Connection]** 確認運作正常，然後按一下 **[!UICONTROL Save Config]**.

您必須刷新Magento快取並重新索引，才能繼續。
