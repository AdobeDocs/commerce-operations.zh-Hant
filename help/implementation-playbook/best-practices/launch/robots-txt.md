---
title: 設定「robots.txt」和「sitemap.xml」檔案的最佳作法
description: 了解如何將Adobe Commerce網站的相關指示傳遞至Web編目程式。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# 設定最佳實務 `robots.txt` 和 `sitemap.xml` 檔案

本文提供使用的最佳實務 `robots.txt` 和 `sitemap.xml` 檔案，包括設定和安全性。 這些檔案會指示網頁機器人（通常是搜尋引擎機器人）如何對網站上的頁面進行編目。 設定這些檔案可改善網站效能和搜尋引擎最佳化。

>[!NOTE]
>
>這些最佳實務僅適用於使用原生Adobe Commerce店面的專案。 不適用於使用其他店面解決方案(例如Adobe Experience Manager、無頭式)的Adobe Commerce專案。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## Adobe Commerce雲基礎架構

預設的Adobe Commerce專案包含階層，包含單一網站、商店和商店檢視。 對於更複雜的實作，您可以為 _多站點_ 店面。

### 單站店

在設定 `robots.txt` 和 `sitemap.xml` 單站點商店的檔案：

- 確定您的專案使用 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 2002.0.12版或更新版本。
- 使用管理應用程式將內容新增至 `robots.txt` 檔案。

   >[!TIP]
   >
   >檢視自動產生的 `robots.txt` 儲存的檔案 `<domain.your.project>/robots.txt`.

- 使用管理應用程式產生 `sitemap.xml` 檔案。

   >[!IMPORTANT]
   >
   >由於雲端基礎架構專案上的Adobe Commerce上是唯讀檔案系統，您必須指定 `pub/media` 路徑。

- 使用自訂的Abmetly VCL程式碼片段，從網站的根目錄重新導向至 `pub/media/` 兩個檔案的位置：

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- 在網頁瀏覽器中檢視檔案，以測試重新導向。 例如， `<domain.your.project>/robots.txt` 和 `<domain.your.project>/sitemap.xml`. 請確定您使用的根路徑是您為設定重新導向的路徑，而非不同的路徑。

>[!INFO]
>
>請參閱 [新增網站地圖和搜尋引擎機器人](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 以取得詳細指示。


### 多地點店面

只要在雲端基礎架構上實作Adobe Commerce，您就可以設定並執行數個商店。 請參閱 [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

設定 `robots.txt` 和 `sitemap.xml` 檔案 [單點店面](#single-site-storefronts) 適用於具有兩個重要差異的多網站店面：

- 請確定 `robots.txt` 和 `sitemap.xml` 檔案名包含相應站點的名稱。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍微修改的自訂Abmetly VCL程式碼片段，從網站的根重新導向至 `pub/media` 兩個檔案在您網站上的位置：

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
   }
   ```

## Adobe Commerce內部

使用管理應用程式來設定 `robots.txt` 和 `sitemap.xml` 防止機器人掃描和索引不必要內容的檔案(請參閱 [搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots))。

>[!TIP]
>
>若是內部部署，您在何處撰寫檔案，取決於您安裝Adobe Commerce的方式。 將檔案寫入 `/path/to/commerce/pub/media/` 或 `/path/to/commerce/media`，以適合您安裝的選項為準。

## 安全性

請勿在 `robots.txt` 檔案。 公開管理員路徑會導致網站遭駭客攻擊及資料可能遺失。 從 `robots.txt` 檔案。

編輯 `robots.txt` 檔案並移除管理路徑的所有項目，請參閱 [行銷使用手冊> SEO和搜尋>搜尋引擎機器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>如果你需要幫助， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.md#submit-ticket).

## 其他資訊

- [了解網站、商店和商店的檢視](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [新增網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [使用Abmetly來封鎖您Adobe Commerce網站的惡意流量](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt在雲端基礎架構2.3.x上的Adobe Commerce中出現404錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.md)
