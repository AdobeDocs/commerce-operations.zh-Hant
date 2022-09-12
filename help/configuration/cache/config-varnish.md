---
title: 配置和使用清漆
description: 了解清漆如何儲存檔案並改善HTTP流量。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# 配置清漆

[清漆快取] 是開放原始碼web應用程式加速器(亦稱為 _HTTP加速器_ 或 _快取HTTP反向代理_)。 清漆可將檔案或檔案片段儲存（或快取）在記憶體中，這樣，清漆可減少未來同等請求的響應時間和網路頻寬消耗。 與Apache和nginx等Web伺服器不同，Quiest是專門用於HTTP通訊協定的。

Commerce 2.4.2使用清漆6.4進行測試。 Commerce 2.4.x與清漆6.x相容

>[!WARNING]
>
>我們 _強烈建議_ 你在生產時用清漆。 內建的全頁快取 — 檔案系統或 [資料庫] — 比Quiest慢很多，而Quiste的設計旨在加速HTTP流量。

有關清漆的詳細資訊，請參閱：

- [清漆大圖]
- [清漆啟動選項]
- [清漆和網站效能]

## 清漆拓撲圖

下圖顯示了Commerce拓撲中Rieshe的基本視圖。

![基本清漆圖](../../assets/configuration/varnish-basic.png)

在上圖中，使用者透過網際網路提出的HTTP要求會產生許多CSS、HTML、JavaScript和影像要求(統稱為 _資產_)。 清漆位於Web伺服器前面，並將這些請求代理到Web伺服器。

當Web伺服器傳回資產時，可快取資產會儲存在Rikest中。 這些資產的任何後續請求都會透過清漆完成（這表示請求不會傳送至Web伺服器）。 清漆可以極快地返回快取內容。 結果會加快將內容傳回給使用者的回應時間，並減少必須由商務履行的請求數量。

由清漆快取的資產會以可設定的間隔過期，或由相同資產的較新版本取代。 您也可以使用 [管理](https://glossary.magento.com/magento-admin) 或 [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令。

## 程式概述

本主題討論如何以最少的參數集初始安裝清漆，並測試其是否有效。 然後從商務管理員匯出清漆設定，並再次測試。

該過程可概括如下：

1. 安裝清漆，並透過存取任何商務頁面來測試，以查看您是否收到指出清漆正在運作的HTTP回應標題。
1. 安裝商務軟體，並使用管理員建立清漆配置檔案。
1. 將現有的清漆設定檔案取代為管理員產生的檔案。
1. 再測試一遍。

   如果您的 `<magento_root>/var/page_cache` 目錄，您已成功配置了Ilest with Commerce!

>[!NOTE]
- 除了另有說明外，您必須以使用者身分輸入本主題中討論的所有命令 `root` 權限。
- 本主題是為CentOS和Apache 2.4上的清漆而編寫的。如果您在不同環境中設定清漆，則某些命令可能會不同。 如需詳細資訊，請參閱清漆檔案。


## 已知問題

我們知道清漆的下列問題：

- [清漆不支援SSL]

   或者，使用SSL終止或SSL終止代理。

- 如果您手動刪除 `<magento_root>/var/cache` 目錄，必須重新啟動清漆。

- 安裝商務時可能出錯：

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   如果您遇到此錯誤，請編輯 `default.vcl` 並將逾時新增至 `backend` 斯坦扎如下：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## 清漆快取概述

清漆快取可與商務搭配使用：

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 從Magento2 GitHub存放庫
- `.htaccess` 隨附Commerce的Apache的分佈式配置檔案
- `default.vcl` 使用 [管理](../cache/config-varnish-magento.md)

>[!INFO]
本主題僅涵蓋前一清單中的預設選項。 在複雜情況下，有許多其他方法可設定快取（例如使用內容傳送網路）;這些方法不在本指南的範圍內。

在第一個瀏覽器請求時，可快取資產會從清漆傳送給用戶端瀏覽器，並在瀏覽器上快取。

此外，清漆使用 [實體](https://glossary.magento.com/entity) 靜態資產的標籤(ETag)。 ETag提供了確定何時 [靜態檔案](https://glossary.magento.com/static-files) 在伺服器上變更。 因此，靜態資產在伺服器上發生變更時（針對來自瀏覽器的新請求或用戶端重新整理瀏覽器快取時）會傳送至用戶端，通常是按F5或Control+F5。

以下各節將提供更多詳細資訊。

## 依瀏覽器要求快取

本節使用瀏覽器偵測器，顯示資產如何在第一個請求中傳遞至瀏覽器，以及之後如何從本機瀏覽器快取載入。

### 第一個瀏覽器請求

`nginx.conf.sample` 和 `.htaccess` 提供用戶端快取選項。 當從瀏覽器對可快取對象提出第一個請求時，清漆會將其傳送給客戶。

下圖顯示了使用瀏覽器檢查器的示例：

![第一次對可快取的物件提出請求時，清漆會將其傳送至瀏覽器](../../assets/configuration/varnish-apache-first-visit.png)

前面的範例顯示對店面首頁(`m2_ce_my`)。 用戶端瀏覽器會快取CSS和JavaScript資產。

>[!NOTE]
大部分的靜態資產都有HTTP 200（確定）狀態代碼，表示已從伺服器擷取資產。

### 第二個瀏覽器請求

如下圖所示，如果相同的瀏覽器再次請求相同頁面，則這些資產會從本機瀏覽器快取傳送。

![下次請求相同物件時，資產會從本機瀏覽器快取載入](../../assets/configuration/varnish-apache-second-visit.png)

請注意第一個和第二個請求的回應時間差異。 靜態資產同樣具有200（確定）回應代碼，因為這是首次從本機快取傳送。

## 商務如何使用Etag

下列範例顯示特定靜態資產的回應標題。

![ETag可讓您更輕鬆判斷靜態資產是否已變更](../../assets/configuration/varnish-etag.png)

`calendar.css` 有一個ETag回應標頭，這表示用戶端瀏覽器上的CSS檔案可與伺服器上的檔案比較。

此外，系統會傳回靜態資產，其中包含304（未修改）HTTP狀態代碼，如下圖所示。

![HTTP 304（未修改）回應代碼指出本機快取中的靜態資產與伺服器上的相同](../../assets/configuration/varnish-304.png)

304狀態代碼的發生是因為用戶使其本地快取失效，且伺服器上的內容未更改。 因為304狀態代碼，靜態資產 _內容_ 未轉讓；只會將HTTP標題下載至瀏覽器。

如果伺服器上的內容變更，用戶端會下載包含HTTP 200（確定）狀態代碼和新ETag的靜態資產。

<!-- Link Definitions -->

[資料庫]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[清漆大圖]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[清漆快取]: https://varnish-cache.org
[清漆啟動選項]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[清漆和網站效能]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[清漆不支援SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
