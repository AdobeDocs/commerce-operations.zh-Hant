---
title: 隱私JavaScript庫
description: 瞭解如何使用自定義工具訪問和刪除Adobe Commerce和Magento Open Source收集的客戶個人資訊。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 隱私JavaScript庫

隱私JavaScript庫是一組工具，可幫助建立訪問和刪除由Adobe Commerce和Magento Open Source收集的私有資料的進程。

商業資料跟蹤服務可以儲存適用於隱私法規的隱私資訊，例如 [一般資料保護法規(GDPR)](gdpr.md) 和 [加利福尼亞消費者隱私法(CCPA)](ccpa.md)。

此庫提供一組用於建立隱私資料請求和收集其響應的功能。 使用此庫可檢索和刪除Adobe Commerce在瀏覽器中儲存的資料，並Magento Open Source資料跟蹤服務。

>[!NOTE]
>
>如果 [Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 啟用後，在購物者同意前，Commerce不會收集行為資料。 如果 [!UICONTROL **Cookie限制模式**] 禁用，Commerce預設收集行為資料。

## 安裝

Privacy JavaScript庫可在以下CDN位置使用： `commerce.adobe.net/magentoprivacy.js`

在您擁有該檔案後，您需要將其添加到Adobe Commerce或Magento Open Source實例中安裝的自定義模組或主題中。 按照 [使用自定義JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 主題完成此任務。

### 初始化

導入並實例化新 `MagentoPrivacy` 或使用 `window` 訪問Privacy JavaScript函式的對象。

示例使用 `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

示例使用 `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## 用法

Privacy JS庫提供各種功能來管理儲存在瀏覽器中的身份資料。

`retrieveIdentity()`
:從瀏覽器中的服務返回標識對象的JavaScript承諾。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
:從瀏覽器中的服務中刪除標識資料。
此函式返回帶有 `isDeleted` boolean屬性，用於指示資料是否已刪除。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
