---
title: 應用程式初始化和引導
description: 閱讀有關Commerce應用程式的初始化和引導邏輯的資訊。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 初始化和引導概覽

若要執行商務應用程式，請在 [pub/index.php][index]:

- 包括 [app/bootstrap.php][bootinitial]，執行基本初始化常式，如錯誤處理、初始化自動載入器、設定分析選項和設定預設時區。
- 建立例項 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 建立Commerce應用程式例項： [\Magento\Framework\AppInterface][app-face]
- 執行商務

## Bootstrap執行邏輯

[引導對象][bootinitial] 使用下列演算法執行商務應用程式：

1. 初始化錯誤處理程式。
1. 建立 [物件管理器][object] 以及基本共用服務，這些服務在任何地方都使用，並受環境影響。 環境參數會正確插入這些物件中。
1. 聲明維護模式為 _not_ 已啟用；否則，終止。
1. 斷言已安裝Commerce應用程式；否則，終止。
1. 啟動商務應用程式。

   應用程式啟動期間未捕獲的任何例外，都會自動傳回至 `catchException()` 方法。 後者也必須返回 `true` 或 `false`:

   - 若 `true`:商務處理異常成功。 不用做別的。
   - 若 `false`:（或任何其他空白結果）商務未處理例外。 引導對象執行預設的異常處理子常式。

1. 傳送應用程式物件提供的回應。

   >[!INFO]
   >
   >Commerce應用程式已安裝且未處於維護模式的斷言是 `\Magento\Framework\App\Bootstrap` 類別。 建立引導對象時，可以使用入口點指令碼修改它。

   修改引導對象的入口點指令碼示例：

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

- 在 [開發人員模式](../bootstrap/application-modes.md#developer-mode)，則依原樣顯示例外狀況。
- 在任何其他模式中，會嘗試記錄例外並顯示一般錯誤訊息。
- 終止商務，但出現錯誤代碼 `1`

## 入口點應用程式

我們有以下入口點應用程式（即由Commerce定義，由Web伺服器用作目錄索引的應用程式）:

### HTTP入口點

[\Magento\Framework\App\Http][http] 運作如下：

1. 決定 [應用區](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. 啟動前控制器和路由系統以查找並執行控制器操作。
1. 使用HTTP回應物件來傳回從控制器動作取得的結果。
1. 錯誤處理（按以下優先順序）:

   1. 如果您使用 [開發人員模式](../bootstrap/application-modes.md#developer-mode):
      - 如果未安裝Commerce應用程式，請重定向至「安裝嚮導」。
      - 如果已安裝Commerce應用程式，則顯示錯誤和HTTP狀態代碼500（內部伺服器錯誤）。
   1. 如果商務應用程式處於維護模式，則顯示用戶友好的「服務不可用」登錄頁，其HTTP狀態代碼為503（服務不可用）。
   1. 如果商務應用程式為 _not_ 已安裝，請重新導向至「安裝精靈」。
   1. 如果工作階段無效，請重新導向至首頁。
   1. 如果有任何其他應用程式初始化錯誤，請顯示一個用戶友好的「找不到頁面」頁，其HTTP狀態代碼為404（找不到）。
   1. 在其他任何錯誤上，顯示HTTP回應503的好記「服務無法使用」頁面，然後產生錯誤報告並在頁面上顯示其ID。

### 靜態資源入口點

[\Magento\Framework\App\StaticResource][static-resource] 是擷取靜態資源（例如CSS、JavaScript和影像）的應用程式。 它會將任何具有靜態資源的動作推遲，直到請求資源為止。

>[!INFO]
>
>靜態檢視檔案的入口點未用於 [生產模式](application-modes.md#production-mode) 以避免伺服器上的潛在木馬程式。 在生產模式中，商務應用程式預期所有必要資源都存在於 `<your Commerce install dir>/pub/static` 目錄。

在預設或開發人員模式中，根據由適當的指定的重寫規則，將對不存在的靜態資源的請求重定向到靜態入口點 `.htaccess`.
當請求被重新導向到入口點時，Commerce應用程式會根據擷取的參數來分析請求的URL，並找到請求的資源。

- 在 [開發人員](application-modes.md#developer-mode) 模式，則會傳回檔案的內容，以便每次請求資源時，傳回的內容都是最新的。
- 在 [預設](application-modes.md#default-mode) 模式，則會發佈擷取的資源，以便由先前請求的URL存取。

   伺服器未來對靜態資源的所有請求都會處理靜態檔案；即，不涉及進入點。 如果需要將已發佈的檔案與原始檔案同步，則 `pub/static` 目錄應移除；因此，檔案會自動隨下一個請求重新發佈。

### 媒體資源入口點

[Magento\MediaStorage\App\Media][media] 從資料庫中檢索媒體資源（即上傳到媒體儲存的任何檔案）。 每當資料庫配置為介質儲存時都會使用它。

`\Magento\Core\App\Media` 嘗試在配置的資料庫儲存中查找媒體檔案，並將其寫入 `pub/static` 目錄，然後返回其內容。 錯誤時，會在標題中傳回HTTP 404（找不到）狀態代碼，但沒有內容。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
