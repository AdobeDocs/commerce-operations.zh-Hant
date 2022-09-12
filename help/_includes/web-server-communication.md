---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全Web伺服器通信

本主題探討如何結合傳輸層安全性(TLS)加密和 [HTTP基本驗證](https://datatracker.ietf.org/doc/html/rfc2617). 您也可以選擇配置其他類型的驗證；我們提供這些資料的參考。

(舊稱安全通訊端層(SSL)，常與TLS交互使用。 在本主題中，我們指 *TLS*.)

>[!WARNING]
>
>除非另有說明，否則本主題中的所有命令必須以用戶身份輸入，其中 `root` 權限。

## Recommendations

我們建議下列項目：

* 您的網站伺服器使用TLS。

   TLS不在本主題的討論範圍內；不過，我們強烈建議您在生產環境中使用真正的憑證，而非自行簽署的憑證。

* 您的搜尋引擎在與Web伺服器相同的主機上執行。 在不同主機上執行搜尋引擎和Web伺服器不在本主題的討論範圍內。

   將搜索引擎和Web伺服器放在同一台主機上的好處是它使得攔截加密通信是不可能的。 搜尋引擎Web伺服器不必與Adobe Commerce或Magento Open SourceWeb伺服器相同；例如，Adobe Commerce可以執行Apache，而Elasticsearch/OpenSearch可以執行nginx。

   如果搜尋引擎公開至公用網路，您應設定驗證。 如果您的搜尋引擎執行個體在網路中受到保護，則可能不需要。 與托管提供者合作，決定您應實作哪些安全措施來保護執行個體。

## 有關TLS的詳細資訊

請參閱下列其中一項資源：

* Apache

   * [Apache 2.4強加密操作](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache上建立SSL憑證以用於Ubuntu 14.04（Digitalocean教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS(CentOS Wiki)設定SSL安全Web伺服器](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL終止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx上建立Ubuntu 14.04的SSL憑證（Digitalocean教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL憑證安裝(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
