---
title: 隱私權JavaScript資料庫
description: 瞭解如何使用自訂工具來存取和刪除Adobe Commerce收集的客戶個人資訊。
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 隱私權JavaScript資料庫

隱私權JavaScript資料庫是一組工具，可協助建立存取和刪除Adobe Commerce所收集私人資料的程式。

Commerce資料追蹤服務可儲存適用於隱私權法規的私人資訊，例如[一般資料保護規範(GDPR)](gdpr.md)和[加州消費者隱私保護法(CCPA)](ccpa.md)。

此程式庫提供一組函式，用於建立隱私權資料請求並收集其回應。 使用此資料庫來擷取和移除瀏覽器中儲存的Adobe Commerce資料追蹤服務資料。

>[!NOTE]
>
>如果啟用[Cookie限制模式](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=zh-Hant)，Commerce會在購物者同意前不會收集行為資料。 如果&#x200B;[!UICONTROL **Cookie限制模式**]&#x200B;已停用，Commerce會依預設收集行為資料。

## 安裝

隱私權JavaScript資料庫可在下列CDN位置使用： `commerce.adobe.net/magentoprivacy.js`

取得檔案後，您需要將其新增到Adobe Commerce執行個體中安裝的自訂模組或主題。 依照[使用自訂JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/)主題中說明的指示完成此工作。

### 初始化

匯入並具現化新的`MagentoPrivacy`物件，或使用`window`物件來存取隱私權JavaScript函式。

使用`import`的範例：

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

使用`window`的範例：

```js
const magePriv = new window.MagentoPrivacy()
```

## 使用狀況

隱私權JS資料庫提供多種功能，可管理儲存在瀏覽器中的身分資料。

`retrieveIdentity()`
：從瀏覽器中的服務傳回身分物件的JavaScript Promise。

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
：從瀏覽器中的服務移除身分資料。
此函式傳回具有`isDeleted`布林值屬性的身分識別物件的JavaScript Promise，以指出資料是否已刪除。

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
