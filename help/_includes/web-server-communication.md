---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全Web伺服器通信

本主題討論了使用傳輸層安全性(TLS)加密和 [HTTP基本身份驗證](https://datatracker.ietf.org/doc/html/rfc2617)。 您也可以選擇配置其他類型的驗證；我們為這些資訊提供參考。

(舊術語「安全套接字層(SSL)」)經常與TLS互換使用。 在本主題中，我們指 *TLS*。)

>[!WARNING]
>
>除非另有說明，否則此主題中的所有命令都必須以用戶身份輸入， `root` 權限。

## Recommendations

我們建議：

* Web伺服器使用TLS。

   TLS超出本主題的範圍；但是，我們強烈建議您在生產中使用實際證書，而不是自簽名證書。

* 您的搜索引擎與Web伺服器在同一主機上運行。 在不同主機上運行搜索引擎和Web伺服器超出本主題的範圍。

   將搜索引擎和Web伺服器放在同一台主機上的優點是，它使攔截加密通信成為不可能。 搜索引擎Web伺服器不必與Adobe Commerce或Magento Open SourceWeb伺服器相同；例如，Adobe Commerce可以運行Apache,Elasticsearch/OpenSearch可以運行nginx。

   如果搜索引擎公開到公共Web，則應配置身份驗證。 如果您的搜索引擎實例在您的網路中受到保護，則可能不需要這樣做。 與您的托管提供商合作，以確定您應實施哪些安全措施來保護您的實例。

## 有關TLS的詳細資訊

請參閱以下資源之一：

* 阿帕奇

   * [Apache 2.4高度加密如何操作](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache上為Ubuntu 14.04建立SSL證書（Digitalocean教程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS(CentOS Wiki)設定SSL安全Web伺服器](https://wiki.centos.org/HowTos/Https)

* 恩金

   * [Nginx SSL終止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx上為Ubuntu 14.04建立SSL證書（Digitalocean教程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL證書安裝(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
