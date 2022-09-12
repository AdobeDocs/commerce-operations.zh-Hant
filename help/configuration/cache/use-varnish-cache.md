---
title: 帶清漆的快取清除
description: 了解快取清除如何與清漆搭配運作，以及如何將其用作Adobe Commerce應用程式的Web快取加速器。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# 帶清漆的快取清除

本主題探討將Uhise當作Adobe Commerce和Magento Open Source的Web快取加速器的基本概念。

## 清漆淨化

根據 [清漆文檔](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *清除* 是當您從 [快取](https://glossary.magento.com/cache) 並連同其變體一起丟棄。」 清漆清除與快取清除命令類似(或按一下 **刷新Magento快取** 中)。

事實上，當您清除、排清或重新整理「商務」快取時，清漆也會清除。

安裝並配置清漆以與Commerce一起使用後，以下操作可能導致清漆清除：

- 維護 [網站](https://glossary.magento.com/website).

   例如，您在「管理員」中執行的任何動作：

   - **商店** > **設定** > **設定** >一般> **一般**
   - **商店** > **設定** > **設定** >一般> **貨幣設定**
   - **商店** > **設定** > **設定** >一般> **儲存電子郵件地址**

   當Commerce偵測到此類變更時，會顯示訊息，通知您重新整理快取。

- 維護商店（例如，添加或編輯類別、價格、產品和促銷定價規則）。

   當您執行任一這些任務時，清漆會自動清除。

- 維護原始碼。

   您應重新整理快取，並定期刪除 `generated/code` 和 `generated/metadata` 目錄。 有關刷新快取的資訊，請參閱下一節。

## 配置商務以清除清漆

在您使用 [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) 命令。

您可以使用選用參數 `--http-cache-hosts` 參數，指定以逗號分隔的清漆主機和偵聽埠清單。 配置所有清漆主機，無論您有一個或多個清漆主機。 （請勿以空格字元分隔主機。）

參數格式必須為 `<hostname or ip>:<listen port>`，此時您可以忽略 `<listen port>` 如果是埠80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

然後，您可以在重新整理「商務」快取時清除清漆主機(亦稱為 *清潔* 快取)，或使用命令列。

若要使用「管理員」重新整理快取，請按一下 **[!UICONTROL SYSTEM]** >工具> **快取管理**，然後按一下 **刷新Magento快取** 頁面頂端。 （您也可以重新整理個別的快取類型。）

若要使用命令列重新整理快取，您通常會使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).
