---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# 安全的Web伺服器通訊

此主題討論使用傳輸層安全性(TLS)加密與[HTTP基本驗證](https://datatracker.ietf.org/doc/html/rfc2617)的組合，保護網頁伺服器與搜尋引擎(Elasticsearch或OpenSearch)之間通訊安全的範例。 您也可以選擇設定其他型別的驗證；我們提供該資訊的參考。

(舊稱Secure Sockets Layer (SSL)，經常與TLS互換使用。 在此主題中，我們稱為&#x200B;*TLS*。)

>[!WARNING]
>
>除非另有說明，否則此主題中的所有命令都必須以具有`root`許可權的使用者身分輸入。

## Recommendations

我們建議以下事項：

* 您的網頁伺服器使用TLS。

  TLS不在本主題的討論範圍內；不過，我們強烈建議您在生產中使用真正的憑證，而不是自我簽署憑證。

* 您的搜尋引擎會在與網頁伺服器相同的主機上執行。 在不同主機上執行搜尋引擎和網頁伺服器不在本主題的討論範圍內。

  將搜尋引擎和網頁伺服器放在同一部主機上的優點是，它無法攔截加密的通訊。 搜尋引擎網頁伺服器不必與Adobe Commerce網頁伺服器相同；例如，Adobe Commerce可以執行Apache，而Elasticsearch/OpenSearch可以執行nginx。

  如果搜尋引擎公開於公用網站，您應該設定驗證。 如果您的搜尋引擎執行個體在網路上受到保護，則可能沒有必要。 請與您的託管提供者合作，決定您應實作哪些安全性措施來保護您的執行個體。

## 更多有關TLS的資訊

請參閱下列資源之一：

* Apache

   * [Apache 2.4高度加密做法](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache for Ubuntu 14.04上建立SSL憑證（Digitalocean教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS (CentOS wiki)設定SSL安全網頁伺服器](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL終止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx上為Ubuntu 14.04建立SSL憑證（Digitalocean教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL憑證安裝(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
