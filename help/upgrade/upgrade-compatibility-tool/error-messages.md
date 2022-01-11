---
title: 升級相容性工具錯誤消息
description: 進一步了解您在Adobe Commerce專案中使用升級相容性工具時遇到的錯誤訊息。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '3759'
ht-degree: 0%

---


# 升級相容性工具錯誤訊息

此錯誤消息參考提供了有關執行升級相容性工具時可能發生的錯誤的資訊。

錯誤訊息會依層級（嚴重問題、錯誤和警告）和類型（核心程式碼、自訂程式碼和GraphQL結構）分類。 每種類型都包含下列資訊：

- **錯誤代碼**:Adobe Commerce為錯誤訊息指派識別碼。
- **錯誤說明**:摘要錯誤原因的說明。
- **錯誤建議的操作**:如果適用，可提供疑難排解和解決錯誤的指引。

## 重大問題

### 核心程式碼

當部分核心檔案遺失或不符合原始檔案時，就會回報這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 2001 |未找到核心檔案 |執行 `composer install` 命令。 | | 2002 |已修改核心檔案 |執行 `composer install` 命令。 | | 2003 |未安裝撰寫器依賴項 |缺少撰寫器相依性可能會導致問題。 通過運行還原依賴性 `composer require package_name`. | | 2005 |未找到核心資料夾 |執行 `composer install` 命令。 |

{style=&quot;table-layout:auto&quot;}

### 自訂程式碼

當自訂程式碼參考目標Adobe Commerce版本中不存在的實體時，會引發嚴重錯誤。 當關鍵編碼標準被破壞時，也會報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1110 |實例化不存在的Adobe Commerce類/介面 |更新代碼以使用標示為 `@api`. 實例化不存在的Adobe Commerce類/介面。 | | 1111 |從不存在的Adobe Commerce類擴展 |擴充類別不再存在於程式碼基底中。 不建議以繼承方式擴充Adobe Commerce功能。 更新代碼以使用標籤為的類 `@api`. | | 1112 |導入不存在的Adobe Commerce類 |更新代碼以使用標示為 `@api`. | | 1113 |載入不存在的Adobe Commerce類 |更新代碼以使用標示為 `@api`. | | 1114 |使用不存在的Adobe Commerce類 |更新代碼以使用標示為 `@api`. | | 1214 |使用不存在的Adobe Commerce常數 |請考慮在自訂程式碼中引入並使用必要值的私人常數。 | | 1215 |覆蓋不存在的Adobe Commerce常數 |請考慮在自訂程式碼中引入並使用必要值的私人常數。 | | 1216 |分配不存在的Adobe Commerce常數 |請考慮在自訂程式碼中引入並使用必要值的私人常數。 | | 1312 |匯入的不存在Adobe Commerce介面 |請考慮移除繼承，或以自訂範圍中引入的介面取代繼承。 | | 1314 |已使用不存在的Adobe Commerce介面 |請考慮移除繼承，或以自訂範圍中引入的介面取代繼承。 | | 1317 |繼承的不存在Adobe Commerce介面 |請考慮移除繼承，或以自訂範圍中引入的介面取代繼承。 | | 1318 |實作的不存在Adobe Commerce介面 |請考慮移除繼承，或以自訂範圍中引入的介面取代繼承。 | | 1410 |呼叫不存在的Adobe Commerce方法 |更新代碼以使用標示為 `@api`. | | 1514 |使用不存在的Adobe Commerce屬性 |更新代碼以使用標示為 `@api`. | | 1515 |覆蓋不存在的Adobe Commerce屬性 |更新代碼以使用標示為 `@api`. | | 1516 |指派不存在的Adobe Commerce屬性 |更新代碼以使用標示為 `@api`. 如果屬性存取層級僅可在單一類別中使用，請將其更新為私用。 | | 5001 |禁止呼叫時間逐項參考呼叫 |在PHP 5.6之後不支援通過引用傳遞。 | | 5002 |開頭的PHP標籤必須是檔案中的第一個內容 |確認PHP開頭標籤之前的檔案中沒有任何內容。 | | 5003 |函式已過時 |使用錯誤訊息中建議的取代。 如果訊息不建議取代，則需要仔細檢閱，以選取替代函式或實作。 | | 5005 | PHP語法錯誤 |必須更新代碼，以符合PHP語法標準。 | | 5008 |可能的Magento2設計違規。 檢測到典型Magento1.x結構 |程式碼需要檢閱和重構。 Magento2框架可能不再支援Magento1結構。 | | 5072 |可能的Magento2設計違規。 檢測到典型Magento1.x結構 |將建構更新為Magento2標準。 | | 5076 |由於自PHP 7起保留命名空間，因此無法在該命名空間中使用 |將命名空間中的保留字替換為非保留關鍵字。 | | 5077 |由於PHP 7已保留，因此不能作為類名使用 |將保留的類名替換為非保留的名稱。 |

{style=&quot;table-layout:auto&quot;}

### GraphQL架構

如果目標版本中不存在架構項，則會引發GraphQL架構關鍵問題。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 3101 |類型已刪除 |列出引用此欄位的所有查詢。 檢查自訂實施是否使用這些查詢。 更新用戶端代碼以處理已變更的查詢介面。 | | 3102 |從聯合中刪除的類型 |如果GraphQL請求建構或回應處理實作中使用聯合類型，則可能需要更新。 | | 3103 |已移除欄位 |檢查自訂程式碼基底中是否參考欄位。 調整實施以正確處理新欄位類型。 | | 3105 |已移除已實作的介面 |檢查自訂是否使用實作移除介面的類型。 如果實作依賴移除的介面，則可能需要更新實作。 | | 3106 |從枚舉中刪除的值 |如果移除的列舉值用於GraphQL請求建構或回應處理實作中，則可能需要更新。 | | 3107 |引數已移除 |檢查欄位是否用於自訂程式碼基底。 移除此欄位的引數。 | | 3109 |已刪除指令 |檢查指令是否用於自定義代碼庫。 調整實施以刪除對指令的引用。 | | 3110 |已刪除指令參數 |檢查指令是否用於自定義代碼庫。 刪除指令參數。 | | 3111 |可重複刪除的指令 |檢查指令是否用於自定義代碼庫。 調整實施以處理介面變更。 | | 3112 |已刪除指令位置 |檢查指令是否用於自定義代碼庫。 調整實施以處理介面變更。 | | 3201 |類型更改類型 |列出引用此欄位的所有查詢。 檢查自訂實施是否使用這些查詢。 更新用戶端代碼以處理已變更的查詢介面。 | | 3203 |欄位更改類型 |檢查自訂程式碼基底中是否參考欄位。 調整實施以正確處理新欄位類型。 | | 3207 |參數更改類型 |檢查欄位是否用於自訂程式碼基底。 更新此欄位的參數類型。 | | 3303 |新增必要的輸入欄位 |如果包含此欄位的查詢用於自訂，則應將欄位新增至請求。 | | 3307 |新增必要引數 |檢查欄位是否用於自訂程式碼基底。 使用欄位時應指定新的必要引數。 | | 3310 |已添加必需指令參數 |檢查指令是否用於自定義代碼庫。 添加指令參數。 |

{style=&quot;table-layout:auto&quot;}

## 錯誤

### 自訂程式碼

自訂程式碼使用未被視為/標示為的Adobe Commerce登入點時，會產生自訂程式碼錯誤 `@api`. 這種入口點的保留行為不能保證。 自訂應依賴 `@api` 登入點。 升級後應測試以非API Adobe Commerce程式碼為基礎的功能。 當主要編碼標準被破壞時，也會報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1104 |使用繼承API介面的非API類別 |未標籤為的類 `@api` 可以變更。 請考慮更新程式碼，以依賴標示為的介面 `@api` 。 否則，依賴此實作的功能應在升級後測試。 | | 1121 |從非Adobe Commerce API類別擴充 |擴充類別不再存在於程式碼基底中。 不建議以繼承方式擴充Adobe Commerce功能。 更新代碼以使用標籤為的類 `@api`. | | 1122 |匯入非Adobe Commerce API類別 |擴充類別不再存在於程式碼基底中。 更新代碼以使用標籤為的類 `@api`. 否則，依賴此實作的功能應在升級後測試。 | | 1123 |載入非Adobe Commerce API類別 |擴充類別不再存在於程式碼基底中。 更新代碼以使用標籤為的類 `@api`. 否則，依賴此實作的功能應在升級後測試。 | | 1124 |使用非Adobe Commerce API類別 |擴充類別不再存在於程式碼基底中。 更新代碼以使用標籤為的類 `@api`. 否則，依賴此實作的功能應在升級後測試。 | | 1224 |使用非Adobe Commerce API常數 |未標示為的常數 `@api` 可以變更。 請考慮在自訂程式碼中引入並使用必要值的專用常數。 | | 1225 |覆寫非Adobe Commerce API常數 |未標示為的常數 `@api` 可以變更。 請考慮在自訂程式碼中引入並使用必要值的專用常數。 | | 1226 |指派非Adobe Commerce API常數 |未標示為的常數 `@api` 可以變更。 請考慮在自訂程式碼中引入並使用必要值的專用常數。 | | 1322 |匯入的非Adobe Commerce API介面 |未標籤為的介面 `@api` 可以變更。 請考慮移除此繼承，或從標示為的Adobe Commerce介面以繼承取代 `@api` 或在自訂代碼範圍中引入的介面。 | | 1324 |使用的非Adobe Commerce API介面 |未標籤為的介面 `@api` 可以變更。 請考慮移除此繼承，或從標示為的Adobe Commerce介面以繼承取代 `@api` 或在自訂代碼範圍中引入的介面。 | | 1327 |繼承的非Adobe Commerce API介面 |未標示為的常數 `@api` 可以變更。 請考慮在自訂程式碼中引入並使用必要值的專用常數。 | | 1328 |已實作非Adobe Commerce API介面 |未標籤為的介面 `@api` 可以變更。 請考慮移除此繼承，或從標示為的Adobe Commerce介面以繼承取代 `@api` 或在自訂代碼範圍中引入的介面。 | | 1420 |實例化非Adobe Commerce API類別/介面 |未標籤為的類 `@api` 可以變更。 請考慮更新程式碼，以依賴標示為的介面 `@api` 。 否則，依賴此實作的功能應在升級後測試。 此外，擷取類別例項的建議方式是使用ID。 如果需要類的新實例，請考慮使用工廠。 | | 1428 |可能依賴於實作詳細資料。 |未標籤為的類 `@api` 可以變更。 請考慮更新程式碼，以依賴標示為的介面 `@api` 。 否則，依賴此實作的功能應在升級後測試。 | | 1429 |呼叫非Adobe Commerce API方法 |未標籤為的方法 `@api` 或未在API類別/介面中宣告皆可變更。 即使方法的介面未在新版本中更新，其行為或輸出也可能不同。 請考慮依賴介面方法。 否則，依賴此實作的功能應在升級後測試。 | | 1449 |呼叫非介面方法（實作中呈現） |未在介面中聲明的方法可以更改。 請考慮依賴介面方法。 否則，依賴此實作的功能應在升級後測試。 | | 1524 |使用非Adobe Commerce API屬性 |未標籤為的屬性值 `@api` 可以變更。 請考慮改用API介面方法。 | | 1525 |覆寫非Adobe Commerce API屬性 |未標籤為的屬性值 `@api` 可以變更。 請考慮改用API介面方法。 | | 1526 |指派非Adobe Commerce API屬性 |未標籤為的屬性值 `@api` 可以變更。 請考慮改用API介面方法。 | | 5004 已棄用無引數的|函式 |傳遞輸入以驗證為函式的第一個引數。 | | 5007 |不鼓勵使用某些功能 |避免使用這些函式。 | | 5009 |模板指令不能調用方法。 只允許標量陣列訪問 |從模板中刪除方法調用。 | | 5010 |範本 `@vars` 注釋區塊包含無效的JSON |修正無效的JSON。 | | 5011 |範本 `@vars` 注釋塊包含無效標籤 |修正無效的標籤。 | | 5012 |範本 `@vars` 註解區塊缺少範本中使用的變數 |將遺漏的變數新增至@vars註解區塊。 | | 5013 |避免搭配非void html元素使用自結標籤 |請改用關閉標籤。 | | 5014 | `"active"` 屬性已過時 |在部署配置中定義活動模組的清單。 | | 5015 | `<param>` 節點已過時 |使用 `<argument name="..." xsi:type="...">` 。 | | 5016 | `<instance>` 節點已過時 |使用 `<argument name="..." xsi:type="object">` 。 | | 5017 | `<array>` 節點已過時 |使用 `<argument name="..." xsi:type="array">` 。 | | 5018 | `<item key="...">` 節點已過時 |使用 `<item name="..." xsi:type="...">` 。 | | 5019 | `<value>` 節點已過時 |請改為提供實際值作為文字常值。 | | 5020 |過期節點： `<supported_blocks>` |將替換為 `<supported_containers>`. | | 5021 |過期節點： `<block_name>` |將替換為 `<container_name>`. | | 5022 |檢測到工廠名稱 |介面工具集類型不應以/開頭。 | | 5023 |在行中檢測到過時的ACL結構 |查看lib/internal/Magento/Framework/Acl/etc/acl.xsd。 | | 5024 |行中檢測到過時的菜單結構 |查看app/code/Magento/Backend/etc/menu.xsd。 | | 5025 |在檔案中檢測到過時的系統配置結構 |查看app/code/Magento/Config/etc/system_file.xsd。 | | 5026 |請勿使用 `"text/javascript"` 類型屬性 |僅使用公共成員。 | | 5027 |通過$this對Block類的成員和方法的訪問在phtml模板中已過時 |僅使用 `$block` 而非 `$this`. | | 5028 |訪問 `Block` 類在phtml模板中已過時 |僅使用公共成員。 | | 5029 |請勿使用 `"jquery/ui"` 範本中的程式庫 |請改用所需的jquery ui介面工具集。 | | 5030 |不初始化PHP中的JS元件 |初始化範本中的JS元件。 | | 5031 |包含過時的方法 |使用 `getConnection()` 方法。 | | 5032 | `loadLayout` 方法已淘汰 |使用 `\Magento\Framework\View\Layout\Builder::build` 。 | | 5033 | `renderLayout` 方法已淘汰 |使用 `\Magento\Framework\Controller\ResultInterface::renderResult` 。 | | 5034 | `_redirect` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Redirect::render` 。 | | 5035 | `_forward` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Forward::forward` 。 | | 5036 | `_setActiveMenu` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::setActiveMenu` 。 | | 5037 | `_addBreadcrumb` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::addBreadcrumb` 。 | | 5038 | `_addContent` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::addContent` 。 | | 5039 | `_addLeft` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::addLeft` 。 | | 5040 | `_addJs` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::addJs` 。 | | 5041 | `_moveBlockToContainer` 方法已淘汰 |使用 `\Magento\Backend\Model\View\Result\Page::moveBlockToContainer` 。 | | 5042 | PHP類引用的格式不正確 |檢查是否僅使用camelCasse字母、數字和無前導斜線引用類。 | | 5043 |模組引用格式不正確 |檢查是否僅使用字母、數字、底線和無前導斜線參考模組。 | | 5044 |類 `Zend_Db_Select` 受限 |建議的替換： `\Magento\Framework\DB\Select`. | | 5045 |類 `Zend_Db_Adapter_Pdo_Mysql` 受限 |建議的替換： `\Magento\Framework\DB\Adapter\Pdo\Mysql`. | | 5046 |類 `Magento\Framework\Serialize\Serializer\Serialize` 受限 |建議的替換： `Magento\Framework\Serialize\SerializerInterface`. | | 5047 |類 `ArrayObject` 受限 |建議的替換：自定義類，擴展自 `ArrayObject` 被覆蓋的序列化/取消序列化方法。 | | 5048 |類 `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` 受限 |建議的替換：建立自定義類的工廠，擴展自 `ArrayObject` 被覆蓋的序列化/取消序列化方法。 | | 5049 |塊 `\Magento\Theme\Block\Html\Head\{Css,Link,Script}` 只允許在「head」區塊內 |驗證節點嵌套的完整性。 | | 5050 |正在引用的塊被刪除 |刪除對塊的引用。 | | 5051 | `output="toHtml"` 已過時 |使用 `output="1"`. | | 5052 |類別 `\Magento\Framework\View\Element\Text\ListText` 不應再在版面中使用 |刪除類 `\Magento\Framework\View\Element\Text\ListText` 。 | | 5053 |通過佈局指令調用方法 `<action>` 不允許 |避免在 `<action>`. | | 5054 | `helper` 屬性包含 `/` |刪除 `/` 從幫助程式屬性。 | | 5055 | `helper` 屬性不包含 `::` |新增 `::` 至協助程式屬性。 | | 5056 |安裝指令碼已過時 |在模組的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5057 | InstallSchema指令碼已過時 |在模組的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5058 | InstallData指令碼已過時 |在模組的「設定」/「修補」/「資料」目錄中使用資料修補程式方法。 | | 5059 |安裝指令碼已過時 |在模組的「設定」資料夾中建立InstallData類。 | | 5060 |升級指令碼已過時 |在模組的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5061 |升級架構指令碼已過時 |在模組的etc/db_schema.xml檔案中使用聲明性架構方法。 | | 5062 |升級資料指令碼已過時 |在模組的「設定」/「修補」/「資料」目錄中使用資料修補程式方法。 | | 5063 |升級指令碼已過時 |在模組的「設定/修補程式/資料」目錄中使用資料修補程式方法。 | | 5064 |循環指令碼已過時 |在模組的「設定」資料夾中建立循環類。 | | 5065 |「data」位於無效目錄中 |在模組的Setup/Patch/Data資料夾中建立資料修補程式，以進行資料升級，或在模組的etc/db_schema.xml檔案中使用聲明性架構方法進行架構更改。 | | 5066 |「sql」位於無效目錄中 |在模組的Setup/Patch/Data資料夾中建立資料修補程式，以進行資料升級，或在模組的etc/db_schema.xml檔案中使用聲明性架構方法進行架構更改。 | | 5067 |由XPath標識的節點已過時 |應更新錯誤中指出的過時XML。 請遵循錯誤訊息中的建議。 | | 5068 |指令 `{{htmlescape}}` 已過時 |使用 `{{var}}` 。 | | 5069 |指令 `{{escapehtml}}` 已過時 |使用 `{{var}}` 。 | | 5070 |不再需要第3個參數 `getChildHtml()` |從呼叫移除第3個參數 `getChildHtml()`. | | 5071 |不再需要第4個參數 `getChildHtml()` |從呼叫移除第4個參數 `getChildHtml()`. | | 5073 |含斜線的舊表名必須固定為直接表名 |請改用直接表格名稱。 | | 5075 |應用程式模組不應使用來自測試模組的類 |從測試模組中刪除類的使用。 | | 5078 |必須在建構子中請求類，否則編譯器將無法查找和生成這些類 |向建構子添加類。 | | 5079 |不鼓勵使用var類別變數 |避免使用&#39;var&#39;來宣告類別變數。 | | 5080 |檢測到可能的原始SQL陳述式 |請改用儲存庫或資料修補程式。 | | 5081 |不鼓勵在模板中使用幫手 |請改用ViewModel。 | | 5082 |不建議在範本中使用$this |請改用$block。 | | 5083 |不允許將常數作為翻譯函式的第一個引數 |請改用字串常值。 | | 5084 |請勿在php中初始化JS元件 |初始化範本中的JS元件。 | | 5085 |不鼓勵使用某些功能 |請改用訊息上建議的替代函式。 | | 5087 | PHP跨版本相容性問題 |請依照訊息中的建議操作，並檢查 [移轉指南](https://www.php.net/manual/en/migration81.php). | | 5088 |在所需參數後找到可選參數 |將所需參數移至選用參數之後。 | | 5089 |方法可見性 `final private` 找到 |將方法可見性從 `final private` 僅限 `private`. | | 5090 |魔術方法 `__set_state` 未定義為 `static` |魔術方法 `__set_state` 必須定義為 `static`. | | 5091 |類，包含 `__toString()` 不繼承 `Stringable` 介面 |新增 `Stringable` 介面與類 `__toString()` 方法。 | | 5092 | `is_resource()` 用於現在傳回物件的函式的方法 |更改 `is_resource()` to `instanceof` 物件。 | | 6001 | `jQuery.andSelf()` 已移除 |使用 `jQuery.addBack()`. | | 6002 | jQuery `$.bind` 和 `$.unbind` 已過時 |使用 `$.on` 和 `$.off` 。 | | 6003 | jQuery方法不建議使用來訂閱事件，因此不應使用 |使用 `.on("event name", fn)` 方法，而非訂閱該事件。 | | 6003 | jQuery方法觸發事件已遭取代，不應使用 |使用 `.trigger("event name")` 方法來觸發該事件。 | | 6004 | jQuery `$.delegate` 和 `$.undelegate` 已過時 |使用 `$.on` 和 `$.off` 。 | | 6005 |(`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`)已移除 |使用(`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`)。 | | 6006 | `jQuery.size()` 已移除 |使用 `jQuery.length`. | | 6007 | `jQuery.trim` 已過時 |使用 `String.prototype.trim`. | | 6008 |(`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`，移除「inlite」主題、「modern」主題) |更新程式碼以與Tinymce5相容。 | | 6009 | `jQuery.isFunction()` 已過時 |在大多數情況下，可以 [x === 「函式」類型]. | | 6009 | `jQuery.type()` 已過時 |替換為相應的類型檢查，如 [x === 「函式」類型]. | | 6009 | `jQuery.isArray()` 已過時 |請改用原生Array.isArray方法。 | | 6009 | `jQuery.parseJSON()` 已過時 |若要剖析JSON字串，請改用原生JSON.parse方法。 | | 6010 |(`jQuery.expr[":"]`, `jQuery.expr.filters`)已過時 |請改用jQuery.expr.presudos。 |

{style=&quot;table-layout:auto&quot;}

## 警告

### 核心程式碼

當核心程式碼基底中出現微小不一致時，會回報這些警告。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 2004 |撰寫器相依性版本不匹配 |問題表示Talon和實際專案中的撰寫器相依性版本不同。 執行以更新相依性 `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### 自訂程式碼

偵測到對已棄用代碼的參考時，會引發自訂代碼警告。 此類參照應替換為支援的延伸點。 請注意 `@see` 建議的已棄用項目的註解。 當次要編碼標準被破壞時，也會報告這些錯誤。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 1131 |從Adobe Commerce延伸 ``@deprecated`` 類 |延伸類別將在未來版本中移除。 不建議以繼承方式擴充Adobe Commerce功能。 更新代碼以使用標籤為的類 `@api`. | | 1132 |匯入Adobe Commerce `@deprecated` 類 |延伸類別將在未來版本中移除。 請考慮使用標示為的Adobe Commerce類別 `@api` 。 | | 1133 |載入Adobe Commerce `@deprecated` 類 |延伸類別將在未來版本中移除。 請考慮使用標示為的Adobe Commerce類別 `@api` 。 | | 1134 |使用Adobe Commerce `@deprecated` 類 |延伸類別將在未來版本中移除。 請考慮使用標示為的Adobe Commerce類別 `@api` 。 | | 1234 |使用Adobe Commerce `@deprecated` 常數 |已棄用的常數將在即將推出的版本中移除。 請考慮使用標示為的常數 `@api` 或實作中的私人常數。 | | 1235 |覆蓋Adobe Commerce `@deprecated` 常數 |已棄用的常數將在即將推出的版本中移除。 請考慮使用標示為的常數 `@api` 或實作中的私人常數。 | | 1236 |指派Adobe Commerce `@deprecated` 常數 |已棄用的常數將在即將推出的版本中移除。 請考慮使用標示為的常數 `@api` 或實作中的私人常數。 | | 1332 |匯入的Adobe Commerce `@deprecated` 介面 |已棄用的介面將在即將推出的版本中移除。 請考慮使用標示為的介面或類 `@api` 。 | | 1334 |已使用Adobe Commerce `@deprecated` 介面 |已棄用的介面將在即將推出的版本中移除。 請考慮使用標示為的介面或類 `@api` 。 | | 1337 |繼承自Adobe Commerce `@deprecated` 介面 |已棄用的介面將在即將推出的版本中移除。 請考慮使用標示為的介面移除介面繼承 `@api` 或實作中引入的介面。 | | 1338 |實作Adobe Commerce `@deprecated` 介面 |已棄用的介面將在即將推出的版本中移除。 請考慮使用標示為的介面移除介面繼承 `@api` 或實作中引入的介面。 | | 1430 |調用未聲明的資料對象方法 |未宣告的神奇方法可能會變更。 請考慮改用介面方法。 | | 1439 |呼叫Adobe Commerce `@deprecated` 方法 |已棄用的方法將在即將推出的版本中移除。 請考慮改用API介面中宣告的方法。 | | 1534 |使用Adobe Commerce `@deprecated` 屬性 |已棄用的方法將在即將推出的版本中移除。 請考慮改用API介面中宣告的方法。 | | 1535 |覆蓋Adobe Commerce `@deprecated` 屬性 |已棄用的屬性將在即將推出的版本中移除。 請考慮依賴API介面中宣告的方法，或改為在實作中使用私人屬性。 | | 1536 |指派Adobe Commerce `@deprecated` 屬性 |已棄用的方法將在即將推出的版本中移除。 請考慮改用API介面中宣告的方法。 | | 5006 |建構子中絕不能顯式請求代理和攔截器 |應將原始類聲明為建構子參數的類型。 偵聽器/代理類將通過框架依賴項注入實現來傳遞。 | | 5074 |已棄用方法的使用 `getResource()` 偵測到（儲存/載入/刪除）資料。 |請改用存放庫。 | | 5086 |不會在常數上宣告可見性 |在所有常數上宣告可見性。 |

{style=&quot;table-layout:auto&quot;}

### GraphQL架構

當新版本的架構中新增其他項目時，會出現GraphQL架構警告。 建議您檢閱實作，查看是否應用於要求。

|錯誤代碼 |錯誤說明 |建議的操作 | | - | - | - | | 3206 |參數預設值已更改 |如果查詢用於自訂，則可能需要明確指定引數值。 | | 3302 |添加到聯合的類型 |類型已新增至聯合。 檢查查詢傳回此聯合類型的結果在實施處理中是否出現，並確定其能夠處理新增的類型。 | | 3304 |已新增可選輸入欄位 |已新增選填輸入欄位。 檢查實作以確保。 | | 3305 |已新增實作介面 |欄位可接受/提供可在實施中考量的詳細資訊。 | | 3306 |新增至列舉的值 |值已新增至列舉。 如果客戶端在枚舉的值上包含switch語句，並且不包含預設大小寫，則此更改可能會導致意外行為。 | | 3308 |已新增選用引數 |如果查詢在自訂中使用新引數，則可能需要將其新增至請求。 |

{style=&quot;table-layout:auto&quot;}
