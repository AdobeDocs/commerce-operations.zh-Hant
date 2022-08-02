---
title: 應用程式初始化和引導
description: 閱讀有關Commerce應用程式的初始化和引導邏輯的資訊。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---


# 初始化和引導概覽

要運行Commerce應用程式，請在 [pub/index.php][index]:

- 包括 [app/bootstrap.php][bootinitial]執行基本的初始化常式，如錯誤處理、初始化自動載入程式、設定分析選項和設定預設時區。
- 建立實例 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 建立Commerce應用程式實例： [\Magento\Framework\AppInterface][app-face]
- 運行商業

## Bootstrap運行邏輯

[引導對象][bootinitial] 使用以下算法運行Commerce應用程式：

1. 初始化錯誤處理程式。
1. 建立 [對象管理器][object] 以及受環境影響的各地使用的基本共用服務。 將環境參數正確地注入到這些對象中。
1. 斷言維護模式為 _不_ 啟用；否則，終止。
1. 聲稱已安裝Commerce應用程式；否則，終止。
1. 啟動Commerce應用程式。

   應用程式啟動期間的任何未捕獲的異常都會自動傳回至Commerce `catchException()` 方法，可用於處理異常。 後者要麼必須返回 `true` 或 `false`:

   - 如果 `true`:已成功處理商業異常。 沒必要做別的事。
   - 如果 `false`:（或其他空結果）Commerce未處理該異常。 引導對象執行預設異常處理子常式。

1. 發送應用程式對象提供的響應。

   >[!INFO]
   >
   >Commerce應用程式已安裝且未處於維護模式的斷言是 `\Magento\Framework\App\Bootstrap` 類。 在建立引導對象時，可以使用入口點指令碼修改它。

   修改引導對象的示例入口點指令碼：

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## 預設異常處理

引導對象指定Commerce應用程式如何處理未捕獲的異常，如下所示：

- 在 [開發者模式](../bootstrap/application-modes.md#developer-mode)，按原樣顯示異常。
- 在任何其它模式下，都嘗試記錄異常並顯示一般錯誤消息。
- 終止Commerce，並返回錯誤代碼 `1`

## 入口點應用程式

我們有以下入口點應用程式（即由Commerce定義的由Web伺服器用作目錄索引的應用程式）:

### HTTP入口點

[\Magento\Framework\App\Http][http] 如下：

1. 確定 [應用區](https://developer.adobe.com/commerce/php/architecture/modules/areas/)。
1. 啟動前控制器和路由系統以查找和執行控制器操作。
1. 使用HTTP響應對象返回從控制器操作獲得的結果。
1. 錯誤處理（按以下優先順序順序）:

   1. 如果您使用 [開發者模式](../bootstrap/application-modes.md#developer-mode):
      - 如果未安裝Commerce應用程式，請重定向至「安裝嚮導」。
      - 如果安裝了Commerce應用程式，則顯示錯誤和HTTP狀態代碼500（內部伺服器錯誤）。
   1. 如果Commerce應用程式處於維護模式，則顯示用戶友好的「服務不可用」登錄頁，HTTP狀態代碼為503（服務不可用）。
   1. 如果Commerce應用程式 _不_ 已安裝，重定向至「安裝嚮導」。
   1. 如果會話無效，請重定向到首頁。
   1. 如果存在任何其他應用程式初始化錯誤，則顯示用戶友好的「未找到頁面」頁，HTTP狀態代碼為404（未找到）。
   1. 在任何其他錯誤上，顯示用戶友好的「服務不可用」頁面，其HTTP響應為503，並生成錯誤報告，並在頁面上顯示其ID。

### 靜態資源入口點

[\Magento\Framework\App\StaticResource][static-resource] 是用於檢索靜態資源（例如，CSS、JavaScript和映像）的應用程式。 它會將所有操作與靜態資源一起延遲，直到請求該資源。

>[!INFO]
>
>靜態視圖檔案的入口點未用於 [生產模式](application-modes.md#production-mode) 以避免伺服器上的潛在漏洞。 在生產模式中，Commerce應用程式希望在 `<your Commerce install dir>/pub/static` 的子菜單。

在預設或開發者模式下，根據由適當的指定的重寫規則將對不存在的靜態資源的請求重定向到靜態入口點 `.htaccess`。
當將請求重定向到入口點時，Commerce應用程式基於檢索到的參數解析請求的URL並查找所請求的資源。

- 在 [開發者](application-modes.md#developer-mode) 模式下，返回檔案的內容，以便每次請求資源時，返回的內容都是最新的。
- 在 [預設](application-modes.md#default-mode) 模式下，將發佈檢索到的資源，以便先前請求的URL可以訪問它。

   以後對靜態資源的所有請求都由伺服器處理，與靜態檔案相同；即不涉及入口點。 如果需要將已發佈檔案與原始檔案同步， `pub/static` 刪除目錄；因此，檔案會自動隨下一個請求重新發佈。

### 媒體資源入口點

[Magento\MediaStorage\App\Media][media] 從資料庫中檢索媒體資源（即上載到媒體儲存的所有檔案）。 每當資料庫配置為 [介質儲存](https://glossary.magento.com/media-storage)。

`\Magento\Core\App\Media` 嘗試在配置的資料庫儲存中查找媒體檔案並將其寫入 `pub/static` 目錄，然後返回其內容。 錯誤時，它返回標頭中沒有內容的HTTP 404（未找到）狀態代碼。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
