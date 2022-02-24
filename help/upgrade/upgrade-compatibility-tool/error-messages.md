---
title: '"[!DNL Upgrade Compatibility Tool] 錯誤消息"'
description: 瞭解有關使用時遇到的錯誤消息的詳細資訊 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '3638'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 錯誤消息

此錯誤消息引用提供了有關在執行 [!DNL Upgrade Compatibility Tool]。

錯誤消息按級別（嚴重問題、錯誤和警告）和類型（核心代碼、自定義代碼和GraphQL架構）分類。 每種類型都包含以下資訊：

- **錯誤代碼**:Adobe Commerce為錯誤消息分配了標識符。
- **錯誤描述**:概述錯誤原因的說明。
- **建議的操作出錯**:如果適用，提供故障排除和解決錯誤的指導。

## 關鍵問題

### 核心代碼

當某些核心檔案丟失或與原始檔案不匹配時，會報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 2001 |找不到核心檔案 |運行 `composer install` 命令。 | | 2002 |核心檔案已修改 |運行 `composer install` 命令。 | | 2003 |未安裝作曲家依賴關係 |缺少合成器依賴項可能導致問題。 通過運行還原依賴項 `composer require package_name`。 | | 2005 |找不到核心資料夾 |運行 `composer install` 命令。 |

{style=&quot;table-layout:auto&quot;&quot;

### 自定義代碼

當自定義代碼引用目標Adobe Commerce版本中不存在的實體時，會引發嚴重錯誤。 當關鍵編碼標準被破壞時，也報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1110 |實例化不存在的Adobe Commerce類/介面 |更新代碼以使用標籤為 `@api`。 實例化不存在的Adobe Commerce類/介面。 | | 1111 |從不存在的Adobe Commerce類擴展 |代碼庫中不再存在擴展類。 不建議使用繼承來擴展Adobe Commerce功能。 更新代碼以使用標籤為 `@api`。 | | 1112 |導入不存在的Adobe Commerce類 |更新代碼以使用標籤為 `@api`。 | | 1113 |載入不存在的Adobe Commerce類 |更新代碼以使用標籤為 `@api`。 | | 1114 |使用不存在的Adobe Commerce類 |更新代碼以使用標籤為 `@api`。 | | 1214 |使用不存在的Adobe Commerce常數 |請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1215 |覆蓋不存在的Adobe Commerce常數 |請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1216 |不存在的Adobe Commerce常數的賦值 |請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1312 |導入的不存在的Adobe Commerce介面 |請考慮刪除繼承或用自定義範圍中引入的介面替換繼承。 | | 1314 |已使用不存在的Adobe Commerce介面 |請考慮刪除繼承或用自定義範圍中引入的介面替換繼承。 | | 1317 |繼承的不存在的Adobe Commerce介面 |請考慮刪除繼承或用自定義範圍中引入的介面替換繼承。 | | 1318 |實現的不存在的Adobe Commerce介面 |請考慮刪除繼承或用自定義範圍中引入的介面替換繼承。 | | 1410 |調用不存在的Adobe Commerce方法 |更新代碼以使用標籤為 `@api`。 | | 1514 |使用不存在的Adobe Commerce屬性 |更新代碼以使用標籤為 `@api`。 | | 1515 |覆蓋不存在的Adobe Commerce屬性 |更新代碼以使用標籤為 `@api`。 | | 1516 |不存在的Adobe Commerce財產的分配 |更新代碼以使用標籤為 `@api`。 如果屬性訪問級別僅可在單個類中使用，則將其更新為私有。 | | 5002 |開啟的PHP標籤必須是檔案中的第一個內容 |確保在PHP開啟標籤之前檔案中沒有內容。 | | 5003 |函式已棄用 |使用錯誤消息中建議的替換項。 如果消息不建議替換，則需要進行關閉審查以選擇替代功能或實施。 | | 5005 | PHP語法錯誤 |必須更新代碼以符合PHP語法標準。 | | 5072 |可能的Magento2設計違規。 檢測到典型Magento1.x結構 |將構造更新為Magento2標準。 | | 5076 |無法在命名空間中使用，因為自PHP 7以來已保留 |將命名空間中的保留字替換為非保留關鍵字。 | | 5077 |不能作為自PHP 7起保留的類名 |將保留類名替換為非保留名稱。 |

{style=&quot;table-layout:auto&quot;&quot;

### GraphQL架構

如果目標版本中不存在架構項，則會引發GraphQL架構關鍵問題。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 3101 |類型已刪除 |列出引用此欄位的所有查詢。 檢查這些查詢是否由自定義實現使用。 更新客戶端代碼以處理更改的查詢介面。 | | 3102 |從聯合中刪除的類型 |如果在GraphQL請求構建或響應處理實現中使用聯合類型，則可能需要更新它。 | | 3103 |欄位已刪除 |檢查自定義代碼庫中是否引用了該欄位。 調整實現以正確處理新欄位類型。 | | 3105 |已實現的介面已刪除 |檢查在自定義中是否使用了實現已刪除介面的類型。 如果實現依賴於已移除的介面，則可能需要更新它。 | | 3106 |從枚舉中刪除的值 |如果刪除的枚舉值在GraphQL請求構造或響應處理實現中使用，則可能需要更新它。 | | 3107 |參數已刪除 |檢查該欄位是否用於自定義代碼庫。 刪除此欄位的參數。 | | 3109 |指令已刪除 |檢查該指令是否在自定義代碼庫中使用。 調整實現以刪除對指令的引用。 | | 3110 |指令參數已刪除 |檢查該指令是否在自定義代碼庫中使用。 刪除指令參數。 | | 3111 |指令可重複刪除 |檢查該指令是否在自定義代碼庫中使用。 調整實現以處理介面更改。 | | 3112 |指令位置已刪除 |檢查該指令是否在自定義代碼庫中使用。 調整實現以處理介面更改。 | | 3201 |類型更改類型 |列出引用此欄位的所有查詢。 檢查這些查詢是否由自定義實現使用。 更新客戶端代碼以處理更改的查詢介面。 | | 3203 |欄位更改類型 |檢查自定義代碼庫中是否引用了該欄位。 調整實現以正確處理新欄位類型。 | | 3207 |參數更改類 |檢查該欄位是否用於自定義代碼庫。 更新此欄位的參數類型。 | | 3303 |已添加必需的輸入欄位 |如果包含此欄位的查詢用於自定義，則應將該欄位添加到請求中。 | | 3307 |已添加必需參數 |檢查該欄位是否用於自定義代碼庫。 使用欄位時應指定新的必需參數。 | | 3310 |已添加必需的指令參數 |檢查該指令是否在自定義代碼庫中使用。 添加指令參數。 |

{style=&quot;table-layout:auto&quot;&quot;

## 錯誤

### 自定義代碼

當自定義代碼使用未被視為/標籤為的Adobe Commerce入口點時，會引發自定義代碼錯誤 `@api`。 這種入口點的保留行為並不保證。 定制應依賴 `@api` 輸入點。 升級後應測試基於非APIAdobe Commerce代碼的功能。 當主要編碼標準被破壞時也報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1104 |使用繼承API介面的非API類 |未標籤為的類 `@api` 可能已更改。 考慮更新代碼以依賴標籤為 `@api` 的雙曲餘切值。 否則，應在升級後測試依賴此實現的功能。 | | 1121 |從非Adobe CommerceAPI類擴展 |代碼庫中不再存在擴展類。 不建議使用繼承來擴展Adobe Commerce功能。 更新代碼以使用標籤為 `@api`。 | | 1122 |導入非Adobe CommerceAPI類 |代碼庫中不再存在擴展類。 更新代碼以使用標籤為 `@api`。 否則，應在升級後測試依賴此實現的功能。 | | 1123 |載入非Adobe CommerceAPI類 |代碼庫中不再存在擴展類。 更新代碼以使用標籤為 `@api`。 否則，應在升級後測試依賴此實現的功能。 | | 1124 |使用非Adobe CommerceAPI類 |代碼庫中不再存在擴展類。 更新代碼以使用標籤為 `@api`。 否則，應在升級後測試依賴此實現的功能。 | | 1224 |使用非Adobe CommerceAPI常數 |未標籤為的常數 `@api` 可能已更改。 請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1225 |覆蓋非Adobe CommerceAPI常數 |未標籤為的常數 `@api` 可能已更改。 請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1226 |非Adobe CommerceAPI常數的分配 |未標籤為的常數 `@api` 可能已更改。 請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1322 |導入的非Adobe CommerceAPI介面 |介面未標籤為 `@api` 可能已更改。 請考慮刪除此繼承，或將其替換為標籤為的Adobe Commerce介面的繼承 `@api` 或在定制代碼範圍中引入的介面。 | | 1324 |使用的非Adobe CommerceAPI介面 |介面未標籤為 `@api` 可能已更改。 請考慮刪除此繼承，或將其替換為標籤為的Adobe Commerce介面的繼承 `@api` 或在定制代碼範圍中引入的介面。 | | 1327 |繼承的非Adobe CommerceAPI介面 |未標籤為的常數 `@api` 可能已更改。 請考慮在自定義代碼中引入並使用所需值的專用常數。 | | 1328 |已實現的非Adobe CommerceAPI介面 |介面未標籤為 `@api` 可能已更改。 請考慮刪除此繼承，或將其替換為標籤為的Adobe Commerce介面的繼承 `@api` 或在定制代碼範圍中引入的介面。 | | 1420 |實例化非Adobe CommerceAPI類/介面 |未標籤為的類 `@api` 可能已更改。 考慮更新代碼以依賴標籤為 `@api` 的雙曲餘切值。 否則，應在升級後測試依賴此實現的功能。 此外，建議的檢索類實例的方法是使用DI。 如果需要類的新實例，請考慮使用工廠。 | | 1428 |可能對實施詳細資訊的依賴性。 |未標籤為的類 `@api` 可能已更改。 考慮更新代碼以依賴標籤為 `@api` 的雙曲餘切值。 否則，應在升級後測試依賴此實現的功能。 | | 1429 |調用非Adobe CommerceAPI方法 |未標籤為的方法 `@api` 或未在API類/介面中聲明，則可能會更改。 即使方法的介面未在新版本中更新，其行為或輸出也可能不同。 請考慮依賴介面方法。 否則，應在升級後測試依賴此實現的功能。 | | 1449 |調用非介面方法（在實現中存在） |未在介面中聲明的方法可能會更改。 請考慮依賴介面方法。 否則，應在升級後測試依賴此實現的功能。 | | 1524 |使用非Adobe CommerceAPI屬性 |未標籤為的屬性的值 `@api` 可能已更改。 請考慮改用API介面方法。 | | 1525 |覆蓋非Adobe CommerceAPI屬性 |未標籤為的屬性的值 `@api` 可能已更改。 請考慮改用API介面方法。 | | 1526 |非Adobe CommerceAPI屬性的分配 |未標籤為的屬性的值 `@api` 可能已更改。 請考慮改用API介面方法。 | | 5004 |沒有參數的函式已棄用 |傳遞輸入以驗證為函式的第一個參數。 | | 5007 |禁止使用某些函式 |避免使用這些函式。 | | 5009 |模板指令不能調用方法。 只允許標量陣列訪問 |從模板中刪除方法調用。 | | 5010 |模板 `@vars` 注釋塊包含無效的JSON |修復無效的JSON。 | | 5011 |模板 `@vars` 注釋塊包含無效標籤 |修復無效標籤。 | | 5012 |模板 `@vars` 注釋塊缺少模板中使用的變數 |將缺少的變數添加到@vars注釋塊。 | | 5013 |避免將自閉標籤與非void html元素一起使用 |請改用「關閉」標籤。 | | 5014 | `"active"` 屬性已過時 |活動模組清單在部署配置中定義。 | | 5015 | `<param>` 節點已過時 |使用 `<argument name="..." xsi:type="...">` 的雙曲餘切值。 | | 5016 | `<instance>` 節點已過時 |使用 `<argument name="..." xsi:type="object">` 的雙曲餘切值。 | | 5017 | `<array>` 節點已過時 |使用 `<argument name="..." xsi:type="array">` 的雙曲餘切值。 | | 5018 | `<item key="...">` 節點已過時 |使用 `<item name="..." xsi:type="...">` 的雙曲餘切值。 | | 5019 | `<value>` 節點已過時 |相反，將實際值作為文本文本提供。 | | 5020 |過時節點： `<supported_blocks>` |替換為 `<supported_containers>`。 | | 5021 |過時節點： `<block_name>` |替換為 `<container_name>`。 | | 5022 |檢測到工廠名稱 |小部件類型不應以/開頭。 | | 5023 |在行中檢測到過時的ACL結構 |查看lib/internal/Magento/Framework/Acl/etc/acl.xsd。 | | 5024 |在行中檢測到過時的菜單結構 |查看app/code/Magento/Backend/etc/menu.xsd。 | | 5025 |在檔案中檢測到過時的系統配置結構 |查看app/code/Magento/Config/etc/system_file.xsd。 | | 5026 |不使用 `"text/javascript"` 類型屬性 |僅使用公共成員。 | | 5028 |訪問受保護和私有成員 `Block` 類在phtml模板中已過時 |僅使用公共成員。 | | 5031 |包含過時方法 |使用 `getConnection()` 的雙曲餘切值。 | | 5032 | `loadLayout` 方法已棄用 |使用 `\Magento\Framework\View\Layout\Builder::build` 的雙曲餘切值。 | | 5033 | `renderLayout` 方法已棄用 |使用 `\Magento\Framework\Controller\ResultInterface::renderResult` 的雙曲餘切值。 | | 5034 | `_redirect` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Redirect::render` 的雙曲餘切值。 | | 5035 | `_forward` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Forward::forward` 的雙曲餘切值。 | | 5036 | `_setActiveMenu` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::setActiveMenu` 的雙曲餘切值。 | | 5037 | `_addBreadcrumb` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::addBreadcrumb` 的雙曲餘切值。 | | 5038 | `_addContent` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::addContent` 的雙曲餘切值。 | | 5039 | `_addLeft` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::addLeft` 的雙曲餘切值。 | | 5040 | `_addJs` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::addJs` 的雙曲餘切值。 | | 5041 | `_moveBlockToContainer` 方法已棄用 |使用 `\Magento\Backend\Model\View\Result\Page::moveBlockToContainer` 的雙曲餘切值。 | | 5042 | PHP類引用的格式不正確 |檢查是否僅使用camelCased字母、數字和無前導斜槓引用該類。 | | 5043 |模組引用的格式不正確 |檢查僅使用字母、數字、下划線和無前導斜槓引用的模組。 | | 5044 |類 `Zend_Db_Select` 受限 |建議的替換： `\Magento\Framework\DB\Select`。 | | 5045 |類 `Zend_Db_Adapter_Pdo_Mysql` 受限 |建議的替換： `\Magento\Framework\DB\Adapter\Pdo\Mysql`。 | | 5046 |類 `Magento\Framework\Serialize\Serializer\Serialize` 受限 |建議的替換： `Magento\Framework\Serialize\SerializerInterface`。 | | 5047 |類 `ArrayObject` 受限 |建議的替換：自定義類，擴展自 `ArrayObject` 已覆蓋的序列化/未序列化方法。 | | 5048 |類 `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` 受限 |建議的替換：建立自定義類的工廠，擴展自 `ArrayObject` 已覆蓋的序列化/未序列化方法。 | | 5050 |正在引用的塊已刪除 |刪除對塊的引用。 | | 5051 | `output="toHtml"` 已過時 |使用 `output="1"`。 | | 5052 |類 `\Magento\Framework\View\Element\Text\ListText` 不應該再用在佈局中 |刪除類 `\Magento\Framework\View\Element\Text\ListText` 的子菜單。 | | 5053 |通過佈局指令調用方法 `<action>` 不允許 |避免在 `<action>`。 | | 5054 | `helper` 屬性 `/` |刪除 `/` 從helper屬性。 | | 5055 | `helper` 屬性不包含 `::` |添加 `::` 幫助程式屬性。 | | 5056 |安裝指令碼已過時 |在模組\的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5057 | InstallSchema指令碼已過時 |在模組\的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5058 | InstallData指令碼已過時 |在模組的「設定/修補程式/資料」目錄中使用資料修補程式方法。 | | 5059 |安裝指令碼已過時 |在模組的Setup資料夾中建立類InstallData。 | | 5060 |升級指令碼已過時 |在模組\的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5061 | UpgradeSchema指令碼已過時 |在模組\的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5062 | UpgradeData指令碼已過時 |在模組的「設定/修補程式/資料」目錄中使用資料修補程式方法。 | | 5063 |升級指令碼已過時 |在模組的「設定/修補程式/資料」目錄中使用資料修補程式方法。 | | 5064 |循環指令碼已過時 |在模組的「設定」資料夾中建立重複類。 | | 5065 |「data」位於無效目錄中 |在模組的Setup/Patch/Data資料夾中建立資料修補程式以進行資料升級，或在模組的etc/db_schema.xml檔案中使用聲明性架構方法進行架構更改。 | | 5066 |「sql」位於無效目錄中 |在模組的Setup/Patch/Data資料夾中建立資料修補程式以進行資料升級，或在模組的etc/db_schema.xml檔案中使用聲明性架構方法進行架構更改。 | | 5067 |由XPath標識的節點已過時 |錯誤中指出的過時XML應更新。 按照錯誤消息中的建議執行操作。 | | 5068 |指令 `{{htmlescape}}` 已過時 |使用 `{{var}}` 的雙曲餘切值。 | | 5069 |指令 `{{escapehtml}}` 已過時 |使用 `{{var}}` 的雙曲餘切值。 | | 5070 |第3個參數不再需要 `getChildHtml()` |從調用中刪除第3個參數 `getChildHtml()`。 | | 5071 |第4個參數不再需要 `getChildHtml()` |從調用中刪除第4個參數 `getChildHtml()`。 | | 5073 |帶斜槓的舊表名必須固定到直接表名 |改用直接表名。 | | 5075 |應用程式模組不應使用test模組中的類 |從test模組中刪除類的使用。 | | 5078 必須在建構子中請求|類，否則編譯器將無法找到並生成這些類 |將類添加到建構子。 | | 5079 |不允許使用var類變數 |避免使用「var」聲明類變數。 | | 5080 |檢測到可能的原始SQL陳述式 |改用儲存庫或資料修補程式。 | | 5081 |不鼓勵在模板中使用幫助程式 |改用ViewModel。 | | 5082 |不建議在模板中使用$this |改用$block。 | | 5083 |不允許將常數作為轉換函式的第一個參數 |改為使用字串文本。 | | 5085 |禁止使用某些函式 |請改用消息上建議的替代函式。 | | 5087 | PHP跨版本相容性問題 |根據郵件中的建議，檢查 [遷移指南](https://www.php.net/manual/en/migration81.php)。 | | 5088 |在所需參數後找到的可選參數 |在可選參數後移動所需參數。 | | 5089 |方法可見性 `final private` 找到 |更改方法的可見性 `final private` 僅 `private`。 | | 5090 |魔術方法 `__set_state` 未定義為 `static` |魔術方法 `__set_state` 必須定義為 `static`。 | | 5091 |類 `__toString()` 不繼承 `Stringable` 介面 |添加 `Stringable` 介面與類 `__toString()` 的雙曲餘切值。 | | 5092 | `is_resource()` 用於現在返回對象的函式的方法 |更改 `is_resource()` 至 `instanceof` 對象。 | | 6001 | `jQuery.andSelf()` 已刪除 |使用 `jQuery.addBack()`。 | | 6002 | jQuery `$.bind` 和 `$.unbind` 已棄用 |使用 `$.on` 和 `$.off` 的雙曲餘切值。 | | 6003 | jQuery方法不建議使用，不應使用 |使用 `.on("event name", fn)` 來訂閱該事件。 | | 6003 | jQuery方法不建議使用以觸發事件，因此不應使用 |使用 `.trigger("event name")` 方法來觸發該事件。 | | 6004 | jQuery `$.delegate` 和 `$.undelegate` 已棄用 |使用 `$.on` 和 `$.off` 的雙曲餘切值。 | | 6005 |(`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`)已刪除 |使用(`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`)。 | | 6006 | `jQuery.size()` 已刪除 |使用 `jQuery.length`。 | | 6007 | `jQuery.trim` 已棄用 |使用 `String.prototype.trim`。 | | 6008 |(`addButton`。 `addContextToolbar`。 `addMenuItem`。 `addSidebar`。 `file_browser_callback`。 `insert_button_items`，「inlite」主題、「mobile」主題、「modern」主題)被刪除 |更新代碼以與tinymce5相容。 | | 6009 | `jQuery.isFunction()` 已棄用 |在大多數情況下，可以用 [typex == &quot;函式&quot;]。 | | 6009 | `jQuery.type()` 已棄用 |替換為相應的類型檢查 [typex == &quot;函式&quot;]。 | | 6009 | `jQuery.isArray()` 已棄用 |請改用本機Array.isArray方法。 | | 6009 | `jQuery.parseJSON()` 已棄用 |要分析JSON字串，請改用本機JSON.parse方法。 | | 6010 |(`jQuery.expr[":"]`。 `jQuery.expr.filters`)已棄用 |請改用jQuery.expr.pseudos。 |

{style=&quot;table-layout:auto&quot;&quot;

## 警告

### 核心代碼

當核心代碼庫中存在輕微不一致時，會報告這些警告。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 2004 |合成器依賴關係版本不匹配 |問題表示Composer依賴項版本在標準和實際項目中不同。 通過運行更新依賴項 `composer update <package_name>`。 |

{style=&quot;table-layout:auto&quot;&quot;

### 自定義代碼

當檢測到對不建議使用的代碼的引用時，會引發自定義代碼警告。 此類參照應替換為支援的延伸點。 注意 `@see` 建議案的已棄用項注釋。 當次要編碼標準被破壞時，也會報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1131 |從Adobe Commerce延伸 ``@deprecated`` 類 |擴展類將在即將到來的版本中刪除。 不建議使用繼承來擴展Adobe Commerce功能。 更新代碼以使用標籤為 `@api`。 | | 1132 |導入Adobe Commerce `@deprecated` 類 |擴展類將在即將到來的版本中刪除。 考慮使用標籤為的Adobe Commerce類 `@api` 的雙曲餘切值。 | | 1133 |載入Adobe Commerce `@deprecated` 類 |擴展類將在即將到來的版本中刪除。 考慮使用標籤為的Adobe Commerce類 `@api` 的雙曲餘切值。 | | 1134 |使用Adobe Commerce `@deprecated` 類 |擴展類將在即將到來的版本中刪除。 考慮使用標籤為的Adobe Commerce類 `@api` 的雙曲餘切值。 | | 1234 |使用Adobe Commerce `@deprecated` 常數 |在即將發佈的版本中將刪除已過時的常數。 考慮使用標籤為 `@api` 或在實施中使用私有常數。 | | 1235 |覆蓋Adobe Commerce `@deprecated` 常數 |在即將發佈的版本中將刪除已過時的常數。 考慮使用標籤為 `@api` 或在實施中使用私有常數。 | | 1236 |Adobe Commerce `@deprecated` 常數 |在即將發佈的版本中將刪除已過時的常數。 考慮使用標籤為 `@api` 或在實施中使用私有常數。 | | 1332 |導入的Adobe Commerce `@deprecated` 介面 |在即將推出的版本中將刪除不建議使用的介面。 考慮使用標籤為 `@api` 的雙曲餘切值。 | | 1334 |已用Adobe Commerce `@deprecated` 介面 |在即將推出的版本中將刪除不建議使用的介面。 考慮使用標籤為 `@api` 的雙曲餘切值。 | | 1337 |繼承自Adobe Commerce `@deprecated` 介面 |在即將推出的版本中將刪除不建議使用的介面。 請考慮使用標籤為 `@api` 或在實現中引入的介面。 | | 1338 |已實施Adobe Commerce `@deprecated` 介面 |在即將推出的版本中將刪除不建議使用的介面。 請考慮使用標籤為 `@api` 或在實現中引入的介面。 | | 1430 |調用未聲明的dataobject方法 |未聲明的幻方法可能會更改。 請考慮改用依賴介面方法。 | | 1439 |致電Adobe Commerce `@deprecated` 方法 |在即將到來的版本中將刪除已過時的方法。 請考慮改用API介面中聲明的方法。 | | 1534 |使用Adobe Commerce `@deprecated` 屬性 |在即將到來的版本中將刪除已過時的方法。 請考慮改用API介面中聲明的方法。 | | 1535 |覆蓋Adobe Commerce `@deprecated` 屬性 |將在即將發佈的版本中刪除已棄用的屬性。 請考慮依賴在API介面中聲明的方法，或在實現中使用私有屬性。 | | 1536 |Adobe Commerce `@deprecated` 屬性 |在即將到來的版本中將刪除已過時的方法。 請考慮改用API介面中聲明的方法。 | | 5006 |建構子中永遠不能顯式請求代理和截獲器 |原始類應聲明為建構子參數的類型。 框架依賴項注入實現將傳遞Interceptor/Proxy類。 | | 5074 |已棄用方法的使用 `getResource()` 檢測到（保存/載入/刪除）資料。 |改用儲存庫。 | | 5086 |不在常數上聲明可見性 |聲明所有常數的可見性。 |

{style=&quot;table-layout:auto&quot;&quot;

### GraphQL架構

將附加項添加到新版本的架構中時，會引發GraphQL架構警告。 建議審查執行情況，看是否應將其用於請求。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 3206 |參數預設值已更改 |如果在自定義中使用查詢，則可能必須顯式指定參數值。 | | 3302 |添加到聯合的類型 |類型已添加到聯合。 檢查處理返回此聯合類型的查詢結果的實現，並確保它能夠處理添加的類型。 | | 3304 |已添加可選輸入欄位 |已添加可選輸入欄位。 檢查實施以確保。 | | 3305 |已添加實現的介面 |該欄位可以接受/提供在實施中可考慮的更多資訊。 | | 3306 |添加到枚舉的值 |已將值添加到枚舉。 如果客戶端包含枚舉值上的switch語句且不包含預設大小寫，則此更改可能會導致意外行為。 | | 3308 |添加的可選參數 |如果查詢在自定義中使用新參數，則可能需要將其添加到請求中。 |

{style=&quot;table-layout:auto&quot;&quot;
