---
title: 需要手動遷移的資料
description: '瞭解在Magento1到Magento2資料遷移期間必須手動遷移的資料以及如何執行遷移。 '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# 需要手動遷移的資料

需要手動遷移的資料有四種：

* 媒體

* [店面](https://glossary.magento.com/storefront) 設計

* [管理](https://glossary.magento.com/admin) 用戶帳戶

* 訪問控制清單(ACL)

## 媒體

本節討論如何手動遷移介質檔案。

### 儲存在資料庫中的媒體檔案

>[!WARNING]
>
>資料庫媒體儲存方法自2.4.3Magento起已棄用。


本節適用於您 *僅* 將媒體檔案儲存到Magento資料庫中。 此步驟應在 [資料遷移](data.md):

1. 以管理員身份登錄到Magento1管理面板。

1. 按一下 **系統** > **配置** >高級> **系統**。

1. 在右窗格中，滾動到 **介質的儲存配置**。

1. 從 **選擇媒體資料庫** 清單，按一下 [介質儲存](https://glossary.magento.com/media-storage) 資料庫。

1. 按一下 **同步**。

然後，在「Magento2管理」面板中重複相同的步驟。

### 檔案系統中的媒體檔案

所有媒體檔案(產品、類別、 [威西威格](https://glossary.magento.com/wysiwyg) 編輯器等)應從 `<your Magento 1 install dir>/media` 至 `<your Magento 2 install dir>/pub/media`。

但是， *不* 複製 `.htaccess` 位於Magento1中的檔案 `media` 的子菜單。 Magento2有自己的 `.htaccess` 應該保留的。

## 店面設計

* 檔案設計(CSS、JS、模板、 [XML](https://glossary.magento.com/xml) 版式)更改其位置和格式

* [佈局](https://glossary.magento.com/layout) 儲存在資料庫中的更新。 通過Magento1管理員放在 [CMS](https://glossary.magento.com/cms) 頁面，CMS小部件， [類別](https://glossary.magento.com/category) 頁面和產品頁面

## 訪問控制清單(ACL)

必須手動重新建立所有：

* Web服務API（SOAP、XML-RPC和REST）的憑據

* 管理用戶帳戶，將其與訪問權限關聯

>[!NOTE]
>
>可以使用 `\Migration\Handler\Timezone` 處理程式。 查看 [後續](follow-up.md) 的子菜單。
