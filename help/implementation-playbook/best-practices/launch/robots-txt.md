---
title: 設定Web編目程式的最佳做法
description: 瞭解如何使用「robots.txt」和「sitemap.xml」檔案，將您的Adobe Commerce網站相關指示傳遞給網頁編目程式。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# 設定Web編目程式的最佳做法

本文提供使用的最佳實務 `robots.txt` 和 `sitemap.xml` Adobe Commerce中的檔案，包括設定和安全性。 這些檔案會指示Web編目程式（通常是搜尋引擎自動機制）如何編目網站上的頁面。 設定這些檔案可改善網站效能和搜尋引擎最佳化。

>[!NOTE]
>
>這些最佳實務僅適用於使用原生Adobe Commerce店面的專案。 它們不適用於使用其他店面解決方案(例如Adobe Experience Manager、Headless)的Adobe Commerce專案。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 雲端基礎結構上的Adobe Commerce

預設Adobe Commerce專案包含階層，其中包含單一網站、商店和商店檢視。 針對更複雜的實作，您可以為建立其他網站、商店和商店檢視 _多網站_ 店面。

### 單一網站店面

設定時，請遵循這些最佳實務 `robots.txt` 和 `sitemap.xml` 單一網站店面的檔案：

- 確定您的專案正在使用 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 2002.0.12版或更新版本。
- 使用管理員應用程式將內容新增至 `robots.txt` 檔案。

  >[!TIP]
  >
  >檢視自動產生的 `robots.txt` 您商店的檔案，位於 `<domain.your.project>/robots.txt`.

- 使用管理員應用程式來產生 `sitemap.xml` 檔案。

  >[!IMPORTANT]
  >
  >由於雲端基礎結構專案上的Adobe Commerce是唯讀檔案系統，您必須指定 `pub/media` 路徑。

- 使用自訂Fastly VCL程式碼片段，從網站的根重新導向至 `pub/media/` 兩個檔案的位置：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- 在網頁瀏覽器中檢視檔案，以測試重新導向。 例如， `<domain.your.project>/robots.txt` 和 `<domain.your.project>/sitemap.xml`. 請確定您使用的是設定重新導向的根路徑，而不是不同的路徑。

>[!INFO]
>
>另請參閱 [新增網站地圖和搜尋引擎自動機制](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 以取得詳細指示。


### 多網站店面

您可以在雲端基礎結構上透過單一實施Adobe Commerce來設定和執行數個存放區。 另請參閱 [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

設定此專案的相同最佳實務 `robots.txt` 和 `sitemap.xml` 檔案 [單一網站店面](#single-site-storefronts) 適用於具有兩個重要差異的多網站店面：

- 確定 `robots.txt` 和 `sitemap.xml` 檔案名稱包含對應網站的名稱。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍作修改的自訂Fastly VCL程式碼片段，從網站的根重新導向至 `pub/media` 這兩個檔案在您網站中的位置：

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

使用管理應用程式來設定 `robots.txt` 和 `sitemap.xml` 防止機器人掃描和索引不必要內容的檔案(請參閱 [搜尋引擎自動機制](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots))。

>[!TIP]
>
>對於內部部署，您編寫檔案的位置取決於您安裝Adobe Commerce的方式。 將檔案寫入 `/path/to/commerce/pub/media/` 或 `/path/to/commerce/media`，以適合您的安裝專案為準。

## 安全性

請勿在下列位置公開您的管理員路徑： `robots.txt` 檔案。 公開管理員路徑是網站駭客活動的弱點，且可能會遺失資料。 從以下位置移除管理員路徑： `robots.txt` 檔案。

如需編輯 `robots.txt` 檔案並移除管理員路徑的所有專案，請參閱 [行銷使用手冊> SEO和搜尋>搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>如果您需要協助， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 其他資訊

- [瞭解網站、商店和商店檢視](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [新增網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [使用Fastly封鎖您Adobe Commerce網站的惡意流量](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt在雲端基礎結構2.3.x上的Adobe Commerce中出現404錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
