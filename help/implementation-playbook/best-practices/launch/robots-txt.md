---
title: 配置「robots.txt」和「sitemap.xml」檔案的最佳做法
description: 瞭解如何將有關您的Adobe Commerce站點的說明傳遞給Web爬網程式。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# 配置的最佳做法 `robots.txt` 和 `sitemap.xml` 檔案

本文提供了使用 `robots.txt` 和 `sitemap.xml` 檔案，包括配置和安全。 這些檔案指導Web自動機（通常是搜索引擎自動機）如何在網站上爬網。 配置這些檔案可以提高站點效能和搜索引擎優化。

>[!NOTE]
>
>這些最佳做法僅適用於使用本地Adobe Commerce店面的項目。 它們不適用於使用其他店面解決方案的Adobe Commerce項目(如Adobe Experience Manager、無頭店)。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## Adobe Commerce在雲基礎架構上

預設的Adobe Commerce項目包含包含單個網站、商店和商店視圖的層次結構。 對於更複雜的實施，您可以為 _多站點_ 店面。

### 單點店面

在配置 `robots.txt` 和 `sitemap.xml` 單點店面的檔案：

- 確保項目正在使用 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 2002.0.12版或更高版本。
- 使用Admin應用程式將內容添加到 `robots.txt` 的子菜單。

   >[!TIP]
   >
   >查看自動生成的 `robots.txt` 儲存的檔案 `<domain.your.project>/robots.txt`。

- 使用Admin應用程式生成 `sitemap.xml` 的子菜單。

   >[!IMPORTANT]
   >
   >由於Adobe Commerce上的雲基礎架構項目的只讀檔案系統，您必須指定 `pub/media` 生成檔案之前的路徑。

- 使用自定義的Affeist VCL代碼段將站點的根目錄重定向到 `pub/media/` 兩個檔案的位置：

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- 通過在Web瀏覽器中查看檔案test重定向。 比如說， `<domain.your.project>/robots.txt` 和 `<domain.your.project>/sitemap.xml`。 確保您使用的是為重定向配置的根路徑，而不是其他路徑。

>[!INFO]
>
>請參閱 [添加站點地圖和搜索引擎自動機](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 的上界。


### 多地點店面

您可以在雲基礎架構上通過Adobe Commerce的單一實施來設定和運行多個儲存。 請參閱 [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)。

配置 `robots.txt` 和 `sitemap.xml` 檔案 [單點店面](#single-site-storefronts) 適用於具有兩個重要差異的多地點店面：

- 確保 `robots.txt` 和 `sitemap.xml` 檔案名包含相應站點的名稱。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍微修改的自定義Abmeist VCL代碼段將站點的根重定向到 `pub/media` 兩個檔案在您站點上的位置：

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

使用Admin應用程式配置 `robots.txt` 和 `sitemap.xml` 防止bot掃描和索引不必要的內容的檔案(請參見 [搜索引擎自動機](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots))。

>[!TIP]
>
>對於內部部署，您編寫檔案的位置取決於您如何安裝Adobe Commerce。 將檔案寫入 `/path/to/commerce/pub/media/` 或 `/path/to/commerce/media`，以適合您安裝的選項。

## 安全

不要在您的 `robots.txt` 的子菜單。 暴露管理路徑是站點駭客攻擊和資料丟失的漏洞。 從 `robots.txt` 的子菜單。

要編輯的步驟 `robots.txt` 檔案並刪除管理路徑的所有條目，請參見 [市場營銷使用手冊> SEO和搜索>搜索引擎自動機](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)。

>[!TIP]
>
>如果你需要幫助， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。

## 其他資訊

- [瞭解網站、商店和商店視圖](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [添加網站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [使用Appriest攔截您的Adobe Commerce站點的惡意通信](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt在Adobe Commerce雲基礎架構2.3.x上顯示404個錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
