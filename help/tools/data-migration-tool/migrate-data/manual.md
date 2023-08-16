---
title: 需要手動移轉的資料
description: 瞭解在Magento1到Magento2資料移轉期間必須手動移轉的資料，以及如何進行移轉。
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# 需要手動移轉的資料

有四種型別的資料需要手動移轉：

* 媒體

* 店面設計

* 管理員使用者帳戶

* 存取控制清單(ACL)

## 媒體

本節討論如何手動移轉媒體檔案。

### 儲存在資料庫中的媒體檔案

>[!WARNING]
>
>自Magento2.4.3起，資料庫媒體儲存方法已過時。


本章節適用於您 *僅限* 如果您將媒體檔案儲存在Magento資料庫中。 此步驟應於以下日期之前執行： [資料移轉](data.md)：

1. 以管理員身分登入Magento1管理面板。

1. 按一下 **系統** > **設定** >進階> **系統**.

1. 在右窗格中，捲動至 **媒體的儲存設定**.

1. 從 **選取媒體資料庫** 清單中，按一下您的媒體儲存資料庫名稱。

1. 按一下 **同步**.

然後，在您的Magento2管理面板中重複相同的步驟。

### 檔案系統中的媒體檔案

所有媒體檔案（產品、類別、WYSIWYG編輯器等的影像）都應從手動複製 `<your Magento 1 install dir>/media` 至 `<your Magento 2 install dir>/pub/media`.

但是，可以 *非* 複製 `.htaccess` Magento1中的檔案 `media` 資料夾。 Magento2有其專屬的 `.htaccess` 應該保留的。

## 店面設計

* 以檔案（CSS、JS、範本、XML配置）進行設計變更了其位置和格式

* 配置更新儲存在資料庫中。 透過CMS頁面、CMS Widget、類別頁面和產品頁面中的Magento1管理員放置

## 存取控制清單(ACL)

您必須手動重新建立全部：

* Web服務API （SOAP、XML-RPC和REST）的認證

* 管理使用者帳戶並將其與存取許可權相關聯

>[!NOTE]
>
>您可以使用來調整資料庫實體的時區 `\Migration\Handler\Timezone` 處理常式。 請參閱 [後續追蹤](follow-up.md) 區段以取得更多詳細資料。
