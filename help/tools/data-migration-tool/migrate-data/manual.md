---
title: 需要手動遷移的資料
description: 了解在Magento1到Magento2資料移轉期間必須手動移轉的資料，以及如何移轉。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 需要手動遷移的資料

需要手動移轉四種資料：

* 媒體

* 店面設計

* 管理員使用者帳戶

* 訪問控制清單(ACL)

## 媒體

本節討論如何手動遷移介質檔案。

### 儲存在資料庫中的媒體檔案

>[!WARNING]
>
>資料庫媒體儲存方法自Magento2.4.3起淘汰。


本節適用於您 *僅限* 如果將媒體檔案儲存在Magento資料庫中。 此步驟應在之前執行 [資料移轉](data.md):

1. 以管理員身分登入「Magento1管理面板」。

1. 按一下 **系統** > **設定** >進階> **系統**.

1. 在右窗格中，滾動到 **介質的儲存配置**.

1. 從 **選擇媒體資料庫** 清單中，按一下媒體儲存資料庫的名稱。

1. 按一下 **同步**.

然後，在「Magento2管理」面板中重複相同步驟。

### 檔案系統中的介質檔案

所有媒體檔案（產品、類別、WYSIWYG編輯器等的影像）應手動從 `<your Magento 1 install dir>/media` to `<your Magento 2 install dir>/pub/media`.

不過，請 *not* 複製 `.htaccess` 位於Magento1中的檔案 `media` 檔案夾。 Magento2有自己的 `.htaccess` 應該保留。

## 店面設計

* 檔案中的設計（CSS、JS、範本、XML配置）已更改其位置和格式

* 配置儲存在資料庫中的更新。 通過Magento1管理員放置在CMS頁面、 CMS介面工具集、類別頁面和產品頁面中

## 訪問控制清單(ACL)

您必須手動重新建立所有：

* Web服務API（SOAP、XML-RPC和REST）的憑證

* 管理用戶帳戶，將其與訪問權限關聯

>[!NOTE]
>
>您可以使用 `\Migration\Handler\Timezone` 處理常式。 請參閱 [後續](follow-up.md) 一節以取得詳細資訊。
