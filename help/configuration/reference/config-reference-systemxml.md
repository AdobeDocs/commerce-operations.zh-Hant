---
title: system.xml參考
description: 了解系統XML檔案如何管理Commerce應用程式配置。
badge: label="Contributed by David Lambauer" type="Informity" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
source-git-commit: d7f32690b25c61fa31a99e6d02f9f1025de2bb99
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 0%

---


# system.xml參考

此 `system.xml` 檔案可讓您管理商務系統設定。 將此主題用作 `system.xml` 檔案。 此 `system.xml` 檔案位於 `etc/adminhtml/system.xml` 在指定的Commerce 2擴充功能中。

下列程式碼片段顯示檔案的裸機架構：

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
>如果想在IDE中進行即時*XSD驗證，可以運行 `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## 索引標籤//區段/群組/欄位

在 `system.xml` 檔案中，可以定義四個彼此相關的不同圖元類型。 以下部分介紹頁簽、節、組和欄位之間的關係。 以下螢幕截圖顯示Admin後端的Commerce 2系統配置。
紅方會標示在 `system.xml` 檔案：

![螢幕擷圖顯示「管理員」中已設定的區段。](../../assets/configuration/magento2-system-configuration.png)

索引標籤可用來在語義上分割不同的設定區域。 每個索引標籤可包含一或多個區段，也可作為子功能表參考。 區段包含一或多個群組。
每個群組會列出一或多個欄位。 您也可以使用群組來新增下列欄位的一般說明。 如前所述，每個群組都可以有一或多個欄位。 欄位是系統配置上下文中最小的實體。

## 標籤

A `<tab>` — 標籤引用系統配置中的現有頁簽或新頁簽。

### 索引標籤屬性參考

A `<tab>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必填 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | 定義參考區段所使用的識別碼。 | `typeId` | 必填 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 讓標籤可翻譯。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型 — 預設為 `text`. | `string` | 可選 |
| `sortOrder` | 定義區段的排序順序。 高數字會將區段推送至頁面底部；低數字會將區段推至頂端。 | `float` | 可選 |
| `class` | 將定義的CSS類添加到呈現的頁簽HTML元素。 | `string` | 可選 |

### 頁簽節點引用

A `<tab>`-Tag可以有下列子項：

| 節點 | 說明 | 類型 |
|---------|------------------------------------------------------|----------|
| `label` | 定義前端顯示的標籤。 | `string` |

### 範例：建立索引標籤

下列程式碼片段示範如何使用範例資料建立新索引標籤。

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

上述程式碼片段會使用識別碼建立新索引標籤 `A_UNIQUE_ID`. 作為 `translate`-attribute已定義，並引用標籤、 `label`-node是可轉換的。 在呈現過程中，CSS類 `a-custom-css-class-to-style-this-tab` 會套用至為此標籤建立的HTML元素。
此 `sortOrder`-attribute，值為 `10` 會在呈現時定義索引標籤在所有索引標籤清單中的位置。

## 章節

A `<section>` — 標籤引用系統配置中的現有或新部分。

### 節屬性參考

A `<section>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義參考區段所使用的識別碼。 | `typeId` | 必填 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 讓標籤可翻譯。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`. | `string` | 可選 |
| `sortOrder` | 定義區段的排序順序。 數量很多，會將區段推送至頁面底部；低數字會將區段推至頂端。 | `float` | 可選 |
| `showInDefault` | 定義區段是否顯示在預設配置範圍中。 指定 `1` 顯示區段和 `0` 來隱藏區段。 | `int` | 可選 |
| `showInStore` | 定義區段是否顯示在儲存層級。 指定 `1` 顯示區段和 `0` 來隱藏區段。 | `int` | 可選 |
| `showInWebsite` | 定義區段是否顯示在網站層級。 指定 `1` 顯示區段和 `0` 來隱藏區段。 | `int` | 可選 |
| `canRestore` | 定義區段是否可還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2起淘汰。 | `bool` | 可選 |
| `extends` | 借由提供其他區段的識別碼，此節點的內容將延伸您參考的區段。 | `string` | 可選 |

### 節節點引用

A `<section>`-Tag可以有下列子項：

| 節點 | 說明 | 類型 |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | 定義前端顯示的標籤。 | `string` |
| `class` | 將定義的CSS類別新增至呈現的區段HTML元素。 | `string` |
| `tab` | 引用關聯的頁簽。 預期索引標籤的ID。 | `typeTabId` |
| `header_css` | 在撰寫本文時，未使用或評估。 | `string` |
| `resource` | 引用ACL資源來提供此部分的權限設定。 | `typeAclResourceId` |
| `group` | 定義一個或多個子組。 | `typeGroup` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `include` | 用於包含其他 `system_include.xsd` 相容的檔案。 通常用於構造大型 `system.xml` 檔案。 | `includeType` |

### 範例：建立區段並將其指派至索引標籤

下列程式碼片段示範建立新區段的基本用法。

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

上述章節定義ID `A_UNIQUE_SECTION_ID`，會顯示在預設設定檢視和商店內容中。 此 `label`-node是可轉換的。 區段與索引標籤與ID相關聯 `A_UNIQUE_ID`. 只有具有ACL中定義權限的用戶才能訪問該部分 `VENDOR_MODULE::path_to_the_acl_resource`.

## 群組

此 `<group>` — 標籤用於將欄位分組。

### 群組屬性參考

A `<group>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義參考群組所使用的識別碼。 | `typeId` | 必填 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 讓標籤可翻譯。 多個欄位應以空格分隔。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`. | `string` | 可選 |
| `sortOrder` | 定義區段的排序順序。 數量很多，會將區段推送至頁面底部；低數字會將區段推至頂端。 | `float` | 可選 |
| `showInDefault` | 定義組是否顯示在預設配置範圍中。 指定 `1` 顯示群組和 `0` 來隱藏群組。 | `int` | 可選 |
| `showInStore` | 定義群組是否顯示在儲存層級。 指定 `1` 顯示群組和 `0` 來隱藏群組。 | `int` | 可選 |
| `showInWebsite` | 定義群組是否顯示在網站層級。 指定 `1` 顯示群組和 `0` 來隱藏群組。 | `int` | 可選 |
| `canRestore` | 定義組是否可以還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2起淘汰。 | `bool` | 可選 |
| `extends` | 通過提供另一組的標識符，此節點的內容將擴展您引用的節。 | `string` | 可選 |

### 組節點引用

A `<group>`-Tag可以有下列子項：

| 節點 | 說明 | 類型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | 定義前端顯示的標籤。 | `string` |
| `fieldset_css` | 將一個或多個CSS類添加到組欄位集。 | `string` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `clone_model` | 指定要克隆欄位的給定模型。 | `typeModel` |
| `clone_fields` | 啟用或停用欄位的複製。 | `int` |
| `help_url` | 不可擴充。 請參閱下文。 | `typeUrl` |
| `more_url` | 不可擴充。 請參閱下文。 | `typeUrl` |
| `demo_link` | 不可擴充。 請參閱下文。 | `typeUrl` |
| `comment` | 在群組標籤下方新增註解。 使用 `<![CDATA[//]]>` HTML。 | `string` |
| `hide_in_single_store_mode` | 群組是否應以單一存放模式顯示。 `1` 隱藏小組； `0` 顯示群組。 | `int` |
| `field` | 定義此群組下應可用的一或多個欄位。 | `field` |
| `group` | 定義一個或多個子組。 | `unbounded` |
| `depends` | 可用來宣告對其他欄位的相依性。 僅當指定欄位的值為 `1`. 此節點預期 `section/group/field`-string。 | `depends` |
| `attribute` | 前端模型可以使用自訂屬性。 通常用來讓指定的前端模型更具動態性。 | `attribute` |
| `include` | 用於包含其他 `system_include.xsd` 相容的檔案。 通常用於構造大型 `system.xml` 檔案。 | `includeType` |

>[!WARNING]
>
>節點 `more_url`, `demo_url` 和 `help_url` 由僅使用一次的PayPal前端模型定義。 這些節點無法重複使用。

### 範例：為指定區段建立群組

下列程式碼片段示範建立新群組的基本用法。

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

上述群組會定義ID `A_UNIQUE_GROUP_ID`，會顯示在預設設定檢視和商店內容中。 兩者， `label` 和 `comment` 標籤為可翻譯。

## 欄位

此 `<field>` — 標籤用於 `<group>` — 用於定義特定配置值的標籤。

### 欄位屬性參考

A `<field>`-Tag可以具有以下屬性：

| 屬性 | 說明 | 類型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定義參考欄位所使用的識別碼。 | `typeId` | 必填 |
| `translate` | 定義應可翻譯的欄位。 提供 `label` 讓標籤可翻譯。 多個欄位應以空格分隔。 | `string` | 可選 |
| `type` | 定義呈現的HTML元素的輸入類型。 預設為 `text`. | `string` | 可選 |
| `sortOrder` | 定義區段的排序順序。 高數字會將區段推送至頁面底部；低數字會將區段推至頂端。 | `float` | 可選 |
| `showInDefault` | 定義欄位是否顯示在預設配置範圍中。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `showInStore` | 定義欄位是否在儲存層級顯示。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `showInWebsite` | 定義欄位是否顯示在網站層級。 指定 `1` 顯示欄位和 `0` 來隱藏欄位。 | `int` | 可選 |
| `canRestore` | 定義欄位是否可還原為預設值。 | `int` | 可選 |
| `advanced` | 自100.0.2起淘汰。 | `bool` | 可選 |
| `extends` | 借由提供其他欄位的識別碼，此節點的內容將延伸您參考的區段。 | `string` | 可選 |

### 欄位類型參考

A `<field>`-Tag可為 `type=""` 屬性：

| 類型 | 說明 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 標準、單行文本欄位 |
| `textarea` | 文字區塊 |
| `select` | 一般的下拉式清單，可能需要自訂 `source_model`. 也用於 `Yes/No` 選取項目。 請參閱 `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` 例如。 |
| `multiselect` | 贊 `select` 但有多個選項有效。 |
| `button` | 觸發立即事件的按鈕。 需要自訂前端模型來定義按鈕文字和動作。 請參閱 `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` 例如。 |
| `obscure` | 值加密且顯示為的文字欄位 `****`. 在瀏覽器中使用「Inspect元素」變更類型時不會顯示值。 |
| `password` | 贊 `obscure` 但隱藏值未加密，且使用瀏覽器中的「Inspect元素」強制變更類型時，就會顯示值。 |
| `file` | 允許上傳檔案以進行處理。 |
| `label` | 顯示標籤，而非可編輯欄位。 當欄位僅可在特定範圍上編輯時（例如，僅儲存視圖級別），請使用此類型。 |
| `time` | 使用三個下拉式清單（小時、分鐘和秒）來設定時間的控制項。 |
| `allowspecific` | 特定國家/地區的多選清單。 需要 `source_model` 例如 `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 允許上傳影像。 |
| `note` | 允許將資訊性備注新增至頁面。 此類型需要 `frontend_model` 來呈現注釋。 |

您也可以建立自訂欄位類型。 這通常是在需要特殊按鈕及動作時執行。 要執行此操作，需要兩個主要元素：

- 在 `adminhtml` 區域
- 設定 `type=""` 到此塊的路徑

塊本身至少需要 `__construct` 方法和 `getElementHtml()` 方法。 此 [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) 是自訂類型的簡單範例。

例如，在OfflineShipping模組中，「匯出」按鈕定義於 `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` 而欄位定義看起來類似：

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### 欄位節點參考

A `<field>`-Tag可以有下列子項：

| 節點 | 說明 | 類型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | 定義前端顯示的標籤。 | `string` |
| `comment` | 在欄位標籤下方新增註解。 使用 `<![CDATA[//]]>` HTML。 | `string` |
| `tooltip` | 可用來描述此欄位意義的另一個可能前端元素。 顯示為欄位旁的小圖示。 | `string` |
| `hint` | 顯示其他資訊。 僅限特定 `frontend_model`. | `string` |
| `frontend_class` | 將定義的CSS類別新增至呈現的區段HTML元素。 | `string` |
| `frontend_model` | 指定不同的前端模型以更改渲染並修改輸出。 | `typeModel` |
| `backend_model` | 指定不同的後端模型，以修改設定的值。 | `typeModel` |
| `source_model` | 指定提供特定值集的不同源模型。 | `typeModel` |
| `config_path` | 可用來覆寫欄位的一般設定路徑。 | `typeConfigPath` |
| `validate` | 定義不同的驗證規則（以空格分隔）。 可用驗證規則的完整參考清單列於下方。 | `string` |
| `can_be_empty` | 使用時機 `type` is `multiselect` 指定欄位可為空。 | `int` |
| `if_module_enabled` | 僅在指定模組啟用時用於顯示欄位。 | `typeModule` |
| `base_url` | 搭配使用 `upload_dir` 檔案上傳。 | `typeUrl` |
| `upload_dir` | 指定上載的目標目錄。 此節點有其他屬性和節點。 先查一下再使用。 | `typeUploadDir` |
| `button_url` | 若 `button_url` 和 `button_label` 已指定。 通常與自訂前端模型搭配使用。 | `typeUrl` |
| `button_label` | 若 `button_label` 和 `button_url` 已指定。 通常與自訂前端模型搭配使用。 | `string` |
| `more_url` | 不可擴充。 請參閱下文。 | `typeUrl` |
| `demo_url` | 不可擴充。 請參閱下文。 | `typeUrl` |
| `hide_in_single_store_mode` | 群組是否應以單一存放模式顯示。 `1` 隱藏小組； `0` 顯示群組。 | `int` |
| `source_service` | 用於填入選取選項的服務。 | `complexType` |
| `options` | 未使用。 可能已棄用。 | `complexType` |
| `depends` | 可用來向其他欄位宣告相依性。 用於在指定欄位的值為 `1`. 此節點預期 `section/group/field`-string。 | `complexType` |
| `attribute` | 前端模型可以使用自訂屬性。 通常用來讓指定的前端模型更具動態性。 | `complexType` |
| `requires` | 不可擴充。 請參閱下文。 | `complexType` |

>[!WARNING]
>
>節點 `more_url`, `demo_url`, `requires` 和 `options` 由不同的核心支付模式定義，且僅使用一次。 這些節點無法重複使用。

### 範例：在指定群組中建立兩個欄位

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

以上範例會建立兩個欄位，分別在預設值和儲存檢視中顯示/可設定。 這兩個欄位都有註解和工具提示，可向使用者說明其用途。 此 `label`-node是可轉換的。
具有識別碼的欄位 `ANOTHER_UNIQUE_FIELD_ID` 在 `if_module_enabled` 全域啟用。 欄位也會根據規則驗證其值 `required-entry` 和 `no-whitespace`.
具有識別碼的欄位 `A_UNIQUE_FIELD_ID` 定義了提供這些值的不同源模型 `Yes` 和 `No`.

### 通用源模型

下列來源模型由Commerce 2 Core提供。 一般來說，源模型更多；下列清單說明最常見的清單。 請注意，這些來源模型需要欄位屬性 `type` 設為 `select` 才能正常運作。

| 源模型 | 說明 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 提供值 `Yes`, `No` 和 `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | 提供值 `Enable`, `Disable`. 將值儲存為 `0` 和 `1` 在資料庫中。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 提供值 `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` 和 `24 Hours`. 值會儲存為整數。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 提供時間格式的值(12 h/24 h)。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 提供值 `Daily`, `Weekly` 和 `Monthly`. 值在資料庫中儲存為 `D`, `W` 和 `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 以ISO 639-1格式（例如en）提供指定語言的2字母代碼的值。 |
| `Magento\Config\Model\Config\Source\Locale` | 提供與上述值類似的值，但與地區設定代碼（例如en_US）相關。 |

### 欄位驗證

欄位可指派一或多個驗證器類別，以確保使用者的輸入符合擴充功能的要求。 驗證規則可與 `<validate>` — 標籤。
下列範例會驗證欄位並新增數個不同的驗證規則。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

可使用下列驗證規則：

| 規則 | 說明 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 僅允許字母、數字、空格或底線。 |
| `integer` | 允許正數或負數的非小數數字。 |
| `ipv4` | 允許有效的IP v4地址。 |
| `ipv6` | 允許有效的IP v6地址。 |
| `letters-only` | 僅允許字母。 例如， `abcABC`. |
| `letters-with-basic-punc` | 僅允許字母或標點符號。<br>必須傳遞下列運算式： `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | 允許（英國）行動電話號碼。 |
| `no-marginal-whitespace` | 不允許值開頭或結尾的空格。 |
| `no-whitespace` | 不允許空格。 |
| `phoneUK` | 允許（英國）電話號碼。 |
| `phoneUS` | 允許（美國）電話號碼。 |
| `required-entry` | 不允許空值(等同於 `validate-no-empty`)。<br>驗證失敗消息：&quot;這是必填欄位。&quot; |
| `time` | 允許24小時格式的有效時間，介於00:00和23:59之間。 例如 `15`, `15:05` 或 `15:05:48`. |
| `time12h` | 允許12小時格式的有效時間，介於12:00 am和11之間:59:59點。 例如 `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | 允許7個或更多字元，使用數字和字母。 |
| `validate-alphanum-with-spaces` | 僅允許使用字母（a-z或A-Z）、數字(0-9)或空格。 |
| `validate-clean-url` | 允許有效的URL。 例如， `https://www.example.com` 或 `www.example.com`. |
| `validate-currency-dollar` | 允許有效（美元）金額。 例如，$100.00。 |
| `validate-data` | 僅允許使用字母（a-z或A-Z）、數字(0-9)或底線(\_)。<br>第一個字元必須是字母。<br>(必須符合運算式： `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>驗證失敗消息：&quot;此欄位中請僅使用字母（a-z或A-Z）、數字(0-9)或底線(\_)，第一個字元應為字母。&quot; |
| `validate-date-au` | 強制使用下列日期格式：dd/mm/yyyy。 例如，2006年3月17日17/03/2006。 |
| `validate-email` | 允許有效的電子郵件地址。 例如， johndoe@domain.com。 |
| `validate-emailSender` | 允許有效的電子郵件地址。 例如， johndoe@domain.com。 |
| `validate-fax` | 允許有效的傳真號碼。 例如123-456-7890。 |
| `validate-no-empty` | 不允許空值(等同於 `requried-entry`)。<br>驗證失敗消息：&quot;空值。&quot; |
| `validate-no-html-tags` | 不允許使用HTML標籤。 |
| `validate-password` | 允許6個或更多字元。 前導和尾隨空格將被忽略。 |
| `validate-phoneLax` | 允許有效的電話號碼。 例如(123)456-7890或123-456-7890。 |
| `validate-phoneStrict` | 允許有效的電話號碼。 例如(123)456-7890或123-456-7890。 |
| `validate-select` | 強制選擇的選項不具有 `null` 值，字串值 `none` 或字串長度0。 |
| `validate-ssn` | 允許有效的（美國）社會安全號碼。 例如123-45-6789。 |
| `validate-street` | 僅允許使用字母（a-z或A-Z）、數字(0-9)、空格和「#」。 |
| `validate-url` | 允許有效的URL。 需要協定(http://、https://或ftp://)。 |
| `validate-xml-identifier` | 允許有效的XML標識符。 例如some_1、block5、id-4。 |
| `validate-zip-us` | 允許有效的（美國）郵遞區號。 例如90602或90602-1234。 |
| `vinUS` | 允許（美國）車輛識別號(VIN)值。 |

### 預設值

欄位的預設值可在模組的 `etc/config.xml` 檔案，請在 `section/group/field_ID` 節點。

#### 範例：設定的預設值 `ANOTHER_UNIQUE_FIELD_ID` （預設範圍）

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

#### 範例：設定的預設值 `ANOTHER_UNIQUE_FIELD_ID` （網站範圍）

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
