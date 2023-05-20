---
title: system.xml引用
description: 瞭解系統XML檔案如何管理Commerce應用程式配置。
badge: label="由David Lambauer提供" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 0%

---

# system.xml引用

的 `system.xml` 檔案允許您管理Commerce系統配置。 將此主題用作 `system.xml` 的子菜單。 的 `system.xml` 檔案位於 `etc/adminhtml/system.xml` 在Commerce 2分機中。

以下代碼段顯示檔案的裸框架：

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>如果要在IDE中進行即時*XSD驗證，可以運行 `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`。

## 制表符//節/組/欄位

在 `system.xml` 檔案中，可以定義相互關聯的四種不同類型的圖元。 下節介紹了制表符、節、組和欄位之間的關係。 以下螢幕快照顯示管理後端的Commerce 2系統配置。
紅色方塊標籤在 `system.xml` 檔案：

![螢幕快照顯示管理中的已配置部分。](../../assets/configuration/magento2-system-configuration.png)

頁籤用於語義上拆分不同的配置區域。 每個頁籤可包含一個或多個節，這些節也可作為子菜單引用。 節包含一個或多個組。
每個組都列出一個或多個欄位。 您還可以使用組為以下欄位添加常規說明。 如前所述，每個組可以具有一個或多個欄位。 欄位是系統配置上下文中最小的實體。

## 頁籤

A `<tab>` — 標籤對系統配置中現有或新頁籤的引用。

### Tab屬性引用

A `<tab>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必需 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | 定義引用節的標識符。 | `typeId` | 要求 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 使標籤可翻譯。 | `string` | 可選 |
| `type` | 定義渲染HTML元素的輸入類型 — 預設為 `text`。 | `string` | 可選 |
| `sortOrder` | 定義節的排序順序。 高數字將部分推到頁面底部；低數量將截面推到頂部。 | `float` | 可選 |
| `class` | 將定義的CSS類添加到呈現的頁籤HTML元素。 | `string` | 可選 |

### 頁籤節點引用

A `<tab>`-Tag可以具有以下子項：

| 節點 | 說明 | 類型 |
|---------|------------------------------------------------------|----------|
| `label` | 定義在前端顯示的標籤。 | `string` |

### 示例：建立頁籤

以下代碼段演示了使用示例資料建立新頁籤。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

上面的代碼段將建立一個帶有標識符的新頁籤 `A_UNIQUE_ID`。 作為 `translate`-attribute已定義並引用標籤， `label`-node是可轉換的。 在呈現過程中，CSS類 `a-custom-css-class-to-style-this-tab` 將應用於為此頁籤建立的HTML元素。
的 `sortOrder`-attribute，其值為 `10` 在呈現時，定義頁籤在所有頁籤清單中的位置。

## 節

A `<section>` — 標籤對系統配置中現有節或新節的引用。

### 節屬性引用

A `<section>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義引用節的標識符。 | `typeId` | 要求 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 使標籤可翻譯。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`。 | `string` | 可選 |
| `sortOrder` | 定義節的排序順序。 高數字會將部分推到頁面底部；低數字會把這個部分推到頂端。 | `float` | 可選 |
| `showInDefault` | 定義節是否顯示在預設配置作用域中。 指定 `1` 顯示節和 `0` 隱藏分區。 | `int` | 可選 |
| `showInStore` | 定義節是否在儲存級別上顯示。 指定 `1` 顯示節和 `0` 隱藏分區。 | `int` | 可選 |
| `showInWebsite` | 定義節是否在網站級別上顯示。 指定 `1` 顯示節和 `0` 隱藏分區。 | `int` | 可選 |
| `canRestore` | 定義是否可將節還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2以來已棄用。 | `bool` | 可選 |
| `extends` | 通過提供另一節的標識符，此節點的內容將擴展您引用的節。 | `string` | 可選 |

### 節節點引用

A `<section>`-Tag可以具有以下子代：

| 節點 | 說明 | 類型 |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | 定義在前端顯示的標籤。 | `string` |
| `class` | 將定義的CSS類添加到呈現的節HTML元素。 | `string` |
| `tab` | 引用關聯的頁籤。 需要頁籤的ID。 | `typeTabId` |
| `header_css` | 在編寫本文時，未使用或評估。 | `string` |
| `resource` | 引用ACL資源來提供此部分的權限設定。 | `typeAclResourceId` |
| `group` | 定義一個或多個子組。 | `typeGroup` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `include` | 用於包括附加 `system_include.xsd` 相容檔案。 通常用於構造大型 `system.xml` 的子菜單。 | `includeType` |

### 示例：建立節並將其分配給頁籤

以下代碼段演示了建立新節的基本用法。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

上述部分定義了ID `A_UNIQUE_SECTION_ID`，在預設配置視圖和儲存上下文中可見。 的 `label`-node是可轉換的。 該節與ID的頁籤關聯 `A_UNIQUE_ID`。 只有具有ACL中定義的權限的用戶才能訪問該部分 `VENDOR_MODULE::path_to_the_acl_resource`。

## 組

的 `<group>`-Tag用於將欄位分組在一起。

### 組屬性引用

A `<group>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義引用組的標識符。 | `typeId` | 要求 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 使標籤可翻譯。 多個欄位應用空格分隔。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`。 | `string` | 可選 |
| `sortOrder` | 定義節的排序順序。 高數字會將部分推到頁面底部；低數字會把這個部分推到頂端。 | `float` | 可選 |
| `showInDefault` | 定義組是否顯示在預設配置作用域中。 指定 `1` 顯示組和 `0` 隱藏組。 | `int` | 可選 |
| `showInStore` | 定義是否在儲存級別上顯示組。 指定 `1` 顯示組和 `0` 隱藏組。 | `int` | 可選 |
| `showInWebsite` | 定義組是否顯示在網站級別。 指定 `1` 顯示組和 `0` 隱藏組。 | `int` | 可選 |
| `canRestore` | 定義組是否可還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2以來已棄用。 | `bool` | 可選 |
| `extends` | 通過提供另一組的標識符，此節點的內容將擴展您引用的節。 | `string` | 可選 |

### 組節點引用

A `<group>`-Tag可以具有以下子代：

| 節點 | 說明 | 類型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | 定義在前端顯示的標籤。 | `string` |
| `fieldset_css` | 將一個或多個CSS類添加到組欄位集。 | `string` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `clone_model` | 指定要克隆欄位的給定模型。 | `typeModel` |
| `clone_fields` | 已啟用或禁用欄位的克隆。 | `int` |
| `help_url` | 不可擴展。 參見下面。 | `typeUrl` |
| `more_url` | 不可擴展。 參見下面。 | `typeUrl` |
| `demo_link` | 不可擴展。 參見下面。 | `typeUrl` |
| `comment` | 在組標籤下添加註釋。 使用 `<![CDATA[//]]>` HTML可以應用。 | `string` |
| `hide_in_single_store_mode` | 組是否應在單儲存模式下可見。 `1` 藏起了這個組； `0` 顯示組。 | `int` |
| `field` | 定義此組下應可用的一個或多個欄位。 | `field` |
| `group` | 定義一個或多個子組。 | `unbounded` |
| `depends` | 可用於聲明對其他欄位的依賴項。 僅當給定欄位的值為 `1`。 此節點需要 `section/group/field`-string。 | `depends` |
| `attribute` | 前端模型可以使用自定義屬性。 通常用於使給定的前向模型更具動態性。 | `attribute` |
| `include` | 用於包括附加 `system_include.xsd` 相容檔案。 通常用於構造大型 `system.xml` 的子菜單。 | `includeType` |

>[!WARNING]
>
>節點 `more_url`。 `demo_url` 和 `help_url` 由只使用一次的PayPal前端模型定義。 這些節點不可重用。

### 示例：為給定節建立組

以下代碼段演示了建立新組的基本用法。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

上述組定義了ID `A_UNIQUE_GROUP_ID`，在預設配置視圖和儲存上下文中可見。 兩者， `label` 和 `comment` 標籤為可翻譯。

## 欄位

的 `<field>` — 標籤在 `<group>` — 用於定義特定配置值的標籤。

### 欄位屬性引用

A `<field>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義引用該欄位的標識符。 | `typeId` | 要求 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 使標籤可翻譯。 多個欄位應用空格分隔。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`。 | `string` | 可選 |
| `sortOrder` | 定義節的排序順序。 高數字將部分推到頁面底部；低數量將截面推到頂部。 | `float` | 可選 |
| `showInDefault` | 定義欄位是否顯示在預設配置作用域中。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `showInStore` | 定義欄位是否在儲存級別上顯示。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `showInWebsite` | 定義欄位是否顯示在網站級別。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `canRestore` | 定義欄位是否可以還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2以來已棄用。 | `bool` | 可選 |
| `extends` | 通過提供另一個欄位的標識符，此節點的內容將擴展您引用的節。 | `string` | 可選 |

### 欄位類型引用

A `<field>`-Tag可以具有以下值 `type=""` 屬性：

| 類型 | 說明 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 標準，單行文本欄位 |
| `textarea` | 文本塊 |
| `select` | 普通下拉清單，可能需要自定義 `source_model`。 也用於 `Yes/No` 選項。 請參閱 `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` 例如， |
| `multiselect` | 像 `select` 但多個選項有效。 |
| `button` | 觸發立即事件的按鈕。 需要自定義前端模型來定義按鈕文本和操作。 請參閱 `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` 例如， |
| `obscure` | 對值加密並顯示為 `****`。 在瀏覽器中使用「Inspect元素」更改類型不會顯示值。 |
| `password` | 像 `obscure` 但隱藏值未加密，並且使用瀏覽器中的「Inspect元素」強制更改類型確實會顯示該值。 |
| `file` | 允許上載檔案以進行處理。 |
| `label` | 顯示標籤，而不是可編輯欄位。 當欄位僅可編輯於特定範圍（例如，僅儲存視圖級別）時，使用此類型。 |
| `time` | 使用三個下拉時間（小時、分鐘和秒）設定時間的控制項。 |
| `allowspecific` | 特定國家的多選清單。 需要 `source_model` 例如 `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 允許上載影像。 |
| `note` | 允許向頁面添加資訊性注釋。 此類型需要 `frontend_model` 的子菜單。 |

也可以建立自定義欄位類型。 通常，當需要具有操作的特殊按鈕時，會執行此操作。 要做到這一點，需要兩個主要要素：

- 在 `adminhtml` 面積
- 設定 `type=""` 到此塊的路徑

塊本身至少需要 `__construct` 方法和 `getElementHtml()` 的雙曲餘切值。 的 [Magento_離線發運](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) 是自定義類型的簡單示例。

例如，在OfflineShipping模組中，「導出」按鈕在中定義 `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` 欄位定義如下：

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### 欄位節點引用

A `<field>`-Tag可以具有以下子代：

| 節點 | 說明 | 類型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | 定義在前端顯示的標籤。 | `string` |
| `comment` | 在欄位標籤下添加註釋。 使用 `<![CDATA[//]]>` HTML可以應用。 | `string` |
| `tooltip` | 另一個可能的前向元素，可用於描述此欄位的含義。 顯示為欄位旁的小表徵圖。 | `string` |
| `hint` | 顯示其他資訊。 僅可用於特定 `frontend_model`。 | `string` |
| `frontend_class` | 將定義的CSS類添加到呈現的節HTML元素。 | `string` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `backend_model` | 指定其他後端模型以修改配置的值。 | `typeModel` |
| `source_model` | 指定提供特定值集的其他源模型。 | `typeModel` |
| `config_path` | 可用於覆蓋欄位的常規配置路徑。 | `typeConfigPath` |
| `validate` | 定義不同的驗證規則（空格分隔）。 下面列出了可用驗證規則的完整參考清單。 | `string` |
| `can_be_empty` | 使用時間 `type` 是 `multiselect` 來指定欄位可以為空。 | `int` |
| `if_module_enabled` | 僅在啟用給定模組時用於顯示欄位。 | `typeModule` |
| `base_url` | 與 `upload_dir` 檔案上載。 | `typeUrl` |
| `upload_dir` | 指定上載的目標目錄。 此節點具有其他屬性和節點。 在用前查查。 | `typeUploadDir` |
| `button_url` | 在 `button_url` 和 `button_label` 。 通常與自定義前端模型結合使用。 | `typeUrl` |
| `button_label` | 在 `button_label` 和 `button_url` 。 通常與自定義前端模型結合使用。 | `string` |
| `more_url` | 不可擴展。 參見下面。 | `typeUrl` |
| `demo_url` | 不可擴展。 參見下面。 | `typeUrl` |
| `hide_in_single_store_mode` | 組是否應在單儲存模式下可見。 `1` 藏起了這個組； `0` 顯示組。 | `int` |
| `source_service` | 用於填充選擇選項的服務。 | `complexType` |
| `options` | 未使用。 可能已棄用。 | `complexType` |
| `depends` | 可用於聲明對其他欄位的依賴項。 僅當給定欄位的值為 `1`。 此節點需要 `section/group/field`-string。 | `complexType` |
| `attribute` | 前端模型可以使用自定義屬性。 通常用於使給定的前向模型更具動態性。 | `complexType` |
| `requires` | 不可擴展。 參見下面。 | `complexType` |

>[!WARNING]
>
>節點 `more_url`。 `demo_url`。 `requires` 和 `options` 由不同核心支付模式定義，且僅使用一次。 這些節點不可重用。

### 示例：在給定組中建立兩個欄位

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

上面的示例將建立兩個欄位，在預設視圖和儲存視圖中都可見/可配置。 這兩個欄位都帶有注釋和工具提示，用於描述它們對用戶的用途。 的 `label`-node是可轉換的。
具有標識符的欄位 `ANOTHER_UNIQUE_FIELD_ID` 在 `if_module_enabled` 全局啟用。 該欄位還根據規則驗證其值 `required-entry` 和 `no-whitespace`。
具有標識符的欄位 `A_UNIQUE_FIELD_ID` 定義不同的源模型，該模型提供 `Yes` 和 `No`。

### 常見源模型

Commerce 2 Core提供了以下源模型。 總的來說，源模型有很多；以下清單介紹了最常見的清單。 請注意，這些源模型需要欄位屬性 `type` 設定為 `select` 才能正常工作。

| 源模型 | 說明 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 提供值 `Yes`。 `No` 和 `Specified`。 |
| `Magento\Config\Model\Config\Source\Enabledisable` | 提供值 `Enable`。 `Disable`。 將值另存為 `0` 和 `1` 的子菜單。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 提供值 `1 Hour`。`2 Hours`。`6 Hours`。`12 Hours` 和 `24 Hours`。 值保存為整數。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 提供時間格式(12 h/24 h)的值。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 提供值 `Daily`。 `Weekly` 和 `Monthly`。 值將保存在資料庫中 `D`。 `W` 和 `M`。 |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 提供ISO 639-1格式（如en）中給定語言的2字母代碼的值。 |
| `Magento\Config\Model\Config\Source\Locale` | 提供與上述值類似的值，但屬於語言環境代碼（例如en_US）。 |

### 欄位驗證

欄位可以分配一個或多個驗證程式類，以確保用戶的輸入滿足擴展的要求。 驗證規則可與 `<validate>` — 標籤。
下面的示例驗證一個欄位並添加幾個不同的驗證規則。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

以下驗證規則可用：

| 規則 | 說明 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 僅允許字母、數字、空格或下划線。 |
| `integer` | 允許正數或負數非十進位數。 |
| `ipv4` | 允許有效的IP v4地址。 |
| `ipv6` | 允許有效的IP v6地址。 |
| `letters-only` | 僅允許字母。 比如說， `abcABC`。 |
| `letters-with-basic-punc` | 僅允許字母或標點符號。<br>必須傳遞以下表達式： `/^[a-z\-.,()\u0027\u0022\s]+$/i`。 |
| `mobileUK` | 允許（英國）行動電話號碼。 |
| `no-marginal-whitespace` | 禁止值開始或結束處的空格。 |
| `no-whitespace` | 禁用空白。 |
| `phoneUK` | 允許一個（英國）電話號碼。 |
| `phoneUS` | 允許一個（美國）電話號碼。 |
| `required-entry` | 不允許空值(等效於驗證 `validate-no-empty`)。<br>驗證失敗消息：&quot;這是必填欄位。&quot; |
| `time` | 允許以24小時格式在00:00到23:59之間有效的時間。 例如 `15`。 `15:05` 或 `15:05:48`。 |
| `time12h` | 允許12小時格式的有效時間，介於12:00至11之間:59:晚上59點。 例如 `3 am`。 `11:30 pm`。 `02:15:00 pm`。 |
| `validate-admin-password` | 允許使用數字和字母的7個或7個以上字元。 |
| `validate-alphanum-with-spaces` | 僅允許使用字母（a-z或A-Z）、數字(0-9)或空格。 |
| `validate-clean-url` | 允許有效的URL。 比如說， `https://www.example.com` 或 `www.example.com`。 |
| `validate-currency-dollar` | 允許有效（美元）金額。 例如，100.00美元。 |
| `validate-data` | 僅允許使用字母（a-z或A-Z）、數字(0-9)或下划線(\_)。<br>第一個字元必須是字母。<br>(必須匹配表達式： `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>驗證失敗消息：&quot;請在此欄位中僅使用字母（a-z或A-Z）、數字(0-9)或下划線(\_)，第一個字元應為字母。&quot; |
| `validate-date-au` | 強制使用以下日期格式：dd/mm/yyyy。 例如，17/03/2006 2006年3月17日。 |
| `validate-email` | 允許有效的電子郵件地址。 例如，johndoe@domain.com。 |
| `validate-emailSender` | 允許有效的電子郵件地址。 例如，johndoe@domain.com。 |
| `validate-fax` | 允許有效的傳真號碼。 例如123-456-7890。 |
| `validate-no-empty` | 不允許空值(等效於驗證 `requried-entry`)。<br>驗證失敗消息：&quot;空值。&quot; |
| `validate-no-html-tags` | 不允許使用HTML標籤。 |
| `validate-password` | 允許6個或6個以上字元。 將忽略前導空格和尾隨空格。 |
| `validate-phoneLax` | 允許有效的電話號碼。 例如，(123)456-7890或123-456-7890。 |
| `validate-phoneStrict` | 允許有效的電話號碼。 例如，(123)456-7890或123-456-7890。 |
| `validate-select` | 強制選擇選項不具有 `null` 值，字串值 `none` 或字串長度為0。 |
| `validate-ssn` | 允許有效（美國）的社會保險號碼。 例如123-45-6789。 |
| `validate-street` | 僅允許使用字母（a-z或A-Z）、數字(0-9)、空格和「#」。 |
| `validate-url` | 允許有效的URL。 協定是必需的(http://、https://或ftp://)。 |
| `validate-xml-identifier` | 允許有效的XML標識符。 例如， something_1、block5、id-4。 |
| `validate-zip-us` | 允許有效（美國）郵遞區號。 例如，90602或90602-1234。 |
| `vinUS` | 允許(US)車輛標識號(VIN)值。 |

### 預設值

可以在模組的 `etc/config.xml` 檔案，方法是在 `section/group/field_ID` 的下界。

#### 示例：設定預設值 `ANOTHER_UNIQUE_FIELD_ID` （預設範圍）

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### 示例：設定預設值 `ANOTHER_UNIQUE_FIELD_ID` （網站範圍）

使用 `websites` 標籤，指定特定網站的預設值。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
