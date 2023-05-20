---
title: 配置和使用清漆
description: 瞭解清漆如何儲存檔案並改進HTTP通信。
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# 配置清漆

[清漆快取] 是開源Web應用程式加速器(也稱為 _HTTP加速器_ 或 _快取HTTP反向代理_)。 清漆在記憶體中儲存（或快取）檔案或檔案片段，這使清漆能夠減少將來等效請求的響應時間和網路頻寬消耗。 與Apache和nginx等Web伺服器不同，Wishet設計為專用於HTTP協定。

商2.4.2用清漆6.4測試。Commerce 2.4.x與清漆6.x相容

>[!WARNING]
>
>我們 _強烈建議_ 你在生產時用清漆。 內置的全頁快取 — 到檔案系統或 [資料庫] — 比清漆慢得多，並且清漆旨在加速HTTP通信。

有關清漆的詳細資訊，請參閱：

- [《大清漆》]
- [清漆啟動選項]
- [清漆與網站效能]

## 清漆拓撲圖

下圖顯示了Commerce拓撲中清漆的基本視圖。

![基本清漆圖](../../assets/configuration/varnish-basic.png)

在上圖中，用戶通過Internet的HTTP請求會導致對CSS、HTML、JavaScript和映像(統稱為 _資產_)。 清漆位於Web伺服器前面，並將這些請求代理到Web伺服器。

當Web伺服器返回資產時，可快取資產將儲存在清漆中。 隨後對這些資產的任何請求都由清漆（意思是，這些請求不會到達Web伺服器）來完成。 清漆返回快取內容的速度非常快。 結果是，將內容返回給用戶的響應時間更快，而且必須由Commerce滿足的請求數量也減少。

由清漆快取的資產以可配置的間隔過期，或由相同資產的較新版本替換。 您還可以使用管理員或 [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) 的子菜單。

## 流程概述

本主題討論如何在最小參數集和test下初始安裝清漆。 然後從Commerce Admin導出清漆配置，並重新test。

該過程可概括如下：

1. 通過訪問任何Commerce頁面來安裝清漆並test清漆，以查看是否獲得指示清漆正在工作的HTTP響應標頭。
1. 安裝Commerce軟體並使用Admin建立清漆配置檔案。
1. 將現有的清漆配置檔案替換為管理員生成的配置檔案。
1. Test一切。

   如果你的 `<magento_root>/var/page_cache` 目錄，您已成功將清漆配置為Commerce!

>[!NOTE]
- 除了注意的以外，您必須以用戶身份輸入本主題中討論的所有命令 `root` 權限。
- 本主題是為Muhist on CentOS和Apache 2.4編寫的。如果要在不同的環境中設定清漆，則某些命令可能不同。 有關詳細資訊，請參閱清漆文檔。


## 已知問題

我們知道清漆的以下問題：

- [清漆不支援SSL]

   作為替代，請使用SSL終端或SSL終端代理。

- 如果手動刪除 `<magento_root>/var/cache` 目錄，必須重新啟動清漆。

- 安裝Commerce時可能出錯：

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   如果遇到此錯誤，請編輯 `default.vcl` 並添加超時 `backend` 斯坦扎如下：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## 清漆快取概述

清漆快取與Commerce配合使用：

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 從Magento2 GitHub儲存庫
- `.htaccess` 隨Commerce提供的Apache的分佈式配置檔案
- `default.vcl` 使用 [管理](../cache/configure-varnish-commerce.md)

>[!INFO]
本主題僅涵蓋前面清單中的預設選項。 在複雜情況下配置快取還有許多其他方法（例如，使用內容傳遞網路）;這些方法超出本指南的範圍。

在第一個瀏覽器請求上，可快取資產從清漆傳送到客戶端瀏覽器並快取在瀏覽器上。

此外，清漆使用實體標籤(ETag)用於靜態資產。 ETag提供了一種確定靜態檔案在伺服器上何時更改的方法。 因此，靜態資產在伺服器上發生更改時即會發送到客戶機 — 無論是在來自瀏覽器的新請求上還是客戶機刷新瀏覽器快取時，通常都按F5或Control+F5。

下面各節提供了更多詳細資訊。

## 按瀏覽器請求快取

此部分使用瀏覽器檢查器來顯示如何在第一個請求中將資產傳送到瀏覽器，以及隨後如何從本地瀏覽器快取載入資產。

### 第一個瀏覽器請求

`nginx.conf.sample` 和 `.htaccess` 提供客戶端快取選項。 當從瀏覽器對可快取對象發出第一個請求時，Wishet會將其發送給客戶端。

下圖顯示了使用瀏覽器檢查器的示例：

![第一次請求可快取的對象時，清漆會將其傳送到瀏覽器](../../assets/configuration/varnish-apache-first-visit.png)

上面的示例顯示了對店面首頁(`m2_ce_my`)。 CSS和JavaScript資產將快取在客戶端瀏覽器上。

>[!NOTE]
大多數靜態資產具有HTTP 200(OK)狀態代碼，表示已從伺服器檢索到該資產。

### 第二個瀏覽器請求

如下圖所示，如果同一瀏覽器再次請求同一頁面，則這些資產將從本地瀏覽器快取中傳送。

![下次請求同一對象時，將從本地瀏覽器快取載入資產](../../assets/configuration/varnish-apache-second-visit.png)

請注意第一個請求和第二個請求之間的響應時間差異。 同樣，靜態資產具有200(OK)響應代碼，因為它們是首次從本地快取中傳送的。

## Commerce如何使用Etag

以下示例顯示特定靜態資產的響應標頭。

![ETag使確定靜態資產是否已更改變得更容易](../../assets/configuration/varnish-etag.png)

`calendar.css` 有一個ETag響應頭，這意味著可以將客戶端瀏覽器上的CSS檔案與伺服器上的CSS檔案進行比較。

此外，靜態資產將返回304（未修改）HTTP狀態代碼，如下圖所示。

![HTTP 304（未修改）響應代碼指示本地快取中的靜態資產與伺服器上的相同](../../assets/configuration/varnish-304.png)

出現304狀態代碼是因為用戶使其本地快取無效，並且伺服器上的內容沒有更改。 由於304狀態代碼，靜態資產 _內容_ 未轉讓；只有HTTP標頭下載到瀏覽器。

如果伺服器上的內容發生更改，客戶端將下載靜態資產，其中包含HTTP 200(OK)狀態代碼和新的ETag。

<!-- Link Definitions -->

[資料庫]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[《大清漆》]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[清漆快取]: https://varnish-cache.org
[清漆啟動選項]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[清漆與網站效能]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[清漆不支援SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
