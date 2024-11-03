---
title: 設定Web編目程式的最佳做法
description: 瞭解如何使用「robots.txt」和「sitemap.xml」檔案，將您的Adobe Commerce網站相關指示傳遞給網頁編目程式。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# 設定Web編目程式的最佳做法

This article provides best practices for using `robots.txt` and `sitemap.xml` files in Adobe Commerce, including configuration and security. These files instruct web crawlers (typically search engine robots) how to crawl pages on a website. Configuring these files can improve site performance and search engine optimization.

>[!NOTE]
>
>These best practices apply to projects using the native Adobe Commerce storefront only. 它們不適用於使用其他店面解決方案(例如Adobe Experience Manager、Headless)的Adobe Commerce專案。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 雲端基礎結構上的Adobe Commerce

預設Adobe Commerce專案包含階層，其中包含單一網站、商店和商店檢視。 對於更複雜的實作，您可以為&#x200B;_多網站_&#x200B;店面建立其他網站、商店和商店檢視。

### Single-site storefronts

Follow these best practices when configuring the `robots.txt` and `sitemap.xml` files for single-site storefronts:

- Make sure that your project is using [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) version 2002.0.12 or later.
- Use the Admin application to add content to the `robots.txt` file.

  >[!TIP]
  >
  >在`<domain.your.project>/robots.txt`檢視您商店的自動產生`robots.txt`檔案。

- 使用Admin應用程式產生`sitemap.xml`檔案。

  >[!IMPORTANT]
  >
  >由於Adobe Commerce在雲端基礎結構專案上的檔案系統為唯讀，您必須在產生檔案之前指定`pub/media`路徑。

- 使用自訂Fastly VCL程式碼片段，將兩個檔案從網站的根重新導向至`pub/media/`位置：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- 在網頁瀏覽器中檢視檔案，以測試重新導向。 例如，`<domain.your.project>/robots.txt`和`<domain.your.project>/sitemap.xml`。 請確定您使用的是設定重新導向的根路徑，而不是不同的路徑。

>[!INFO]
>
>如需詳細指示，請參閱[新增網站地圖和搜尋引擎自動機制](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。


### Multi-site storefronts

您可以在雲端基礎結構上透過單一實施Adobe Commerce來設定和執行數個存放區。 請參閱[設定多個網站或商店](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)。

The same best practices for configuring the `robots.txt` and `sitemap.xml` files for [single-site storefronts](#single-site-storefronts) applies to multi-site storefronts with two important differences:

- 請確定`robots.txt`和`sitemap.xml`檔案名稱包含對應網站的名稱。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍作修改的自訂Fastly VCL程式碼片段，將兩個檔案從網站的根重新導向至`pub/media`位置：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce內部部署

使用管理應用程式來設定`robots.txt`和`sitemap.xml`檔案，以防止機器人掃描和索引不必要的內容（請參閱[搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)）。

>[!TIP]
>
>對於內部部署，您編寫檔案的位置取決於您安裝Adobe Commerce的方式。 將檔案寫入`/path/to/commerce/pub/media/`或`/path/to/commerce/media` （選擇適合您安裝的專案）。

## 安全性

Do not expose your Admin path in your `robots.txt` file. Having the Admin path exposed is a vulnerability for site hacking and potential loss of data. Remove the Admin path from the `robots.txt` file.

For steps to edit the `robots.txt` file and remove all entries of the Admin path, see [Marketing User Guide > SEO and Search > Search Engine Robots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>If you need help, [submit an Adobe Commerce Support ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 其他資訊

- [Understanding websites, stores, and store views](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Adding websites](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Use Fastly to block malicious traffic for your Adobe Commerce sites](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt gives a 404 error in Adobe Commerce on cloud infrastructure 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
