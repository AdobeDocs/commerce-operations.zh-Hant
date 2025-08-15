---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 驗證通訊是否安全

本節將討論驗證HTTP基本驗證是否正常運作的兩種方式：

* 使用`curl`命令來驗證您必須輸入使用者名稱和密碼才能取得叢集狀態
* 在Admin中設定HTTP基本驗證

## 使用`curl`命令來驗證叢集狀態

輸入下列命令：

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如，如果您在搜尋引擎伺服器上輸入命令，且您的Proxy使用連線埠8080：

```bash
curl -i http://localhost:8080/_cluster/health
```

下列訊息會顯示以指出驗證失敗：

```
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

現在嘗試下列命令：

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如：

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

這次命令會成功，並出現類似下列的訊息：

```
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 在Admin中設定HTTP基本驗證

執行[搜尋引擎組態](../configuration/search/configure-search-engine.md) *中討論過的相同工作（除了*），請從&#x200B;**[!UICONTROL Yes]**&#x200B;清單中按一下&#x200B;**[!UICONTROL Enable HTTP Auth]**，然後在提供的欄位中輸入您的使用者名稱和密碼。

按一下「**[!UICONTROL Test Connection]**」以確認其運作正常，然後按一下「**[!UICONTROL Save Config]**」。

您必須先清除快取並重新索引，才能繼續。
