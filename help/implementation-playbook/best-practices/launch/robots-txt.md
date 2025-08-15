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

本文提供在Adobe Commerce中使用`robots.txt`和`sitemap.xml`檔案的最佳實務，包括設定和安全性。 這些檔案會指示Web編目程式（通常是搜尋引擎自動機制）如何編目網站上的頁面。 設定這些檔案可改善網站效能和搜尋引擎最佳化。

>[!NOTE]
>
>這些最佳實務僅適用於使用原生Adobe Commerce店面的專案。 它們不適用於使用其他店面解決方案(例如Adobe Experience Manager、Headless)的Adobe Commerce專案。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 雲端基礎結構上的Adobe Commerce

預設Adobe Commerce專案包含階層，其中包含單一網站、商店和商店檢視。 對於更複雜的實作，您可以為&#x200B;_多網站_&#x200B;店面建立其他網站、商店和商店檢視。

### 單一網站店面

設定單一網站店面的`robots.txt`和`sitemap.xml`檔案時，請遵循下列最佳實務：

- 確定您的專案使用[`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) 2002.0.12版或更新版本。
- 使用Admin應用程式新增內容至`robots.txt`檔案。

  >[!TIP]
  >
  >在`robots.txt`檢視您商店的自動產生`<domain.your.project>/robots.txt`檔案。

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


### 多網站店面

您可以在雲端基礎結構上透過單一實施Adobe Commerce來設定和執行數個存放區。 請參閱[設定多個網站或商店](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)。

為`robots.txt`單一網站店面`sitemap.xml`設定[和](#single-site-storefronts)檔案的相同最佳實務適用於具有兩個重要差異的多網站店面：

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

請勿在您的`robots.txt`檔案中公開您的管理員路徑。 公開管理員路徑是網站駭客活動的弱點，且可能會遺失資料。 從`robots.txt`檔案中移除管理員路徑。

如需編輯`robots.txt`檔案及移除管理員路徑之所有專案的步驟，請參閱[行銷使用手冊> SEO與搜尋>搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)。

>[!TIP]
>
>若您需要協助，請[提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。

## 其他資訊

- [瞭解網站、商店和商店檢視](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [正在新增網站](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [使用Fastly封鎖您Adobe Commerce網站的惡意流量](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt在雲端基礎結構2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)上的Adobe Commerce中發生404錯誤
