---
title: 使用清漆清除快取
description: 瞭解快取清除如何與清漆配合使用，以及如何將其用作Adobe Commerce應用程式的Web快取加速器。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# 使用清漆清除快取

本主題討論將清漆用作Adobe Commerce和Magento Open Source的Web快取加速器的基礎知識。

## 清漆清洗

根據 [清漆文檔](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *清除* 從中選取對象時 [快取](https://glossary.magento.com/cache) 把它和它的變體一起丟棄。」 清漆清除類似於快取清除命令(或按一下 **刷新Magento快取** )的正文。

事實上，當您清理、刷新或刷新Commerce快取時，清漆也會清除。

安裝並配置清漆以與Commerce配合使用後，以下操作可導致清漆清除：

- 維護 [網站](https://glossary.magento.com/website)。

   例如，您在管理中執行的任何操作：

   - **商店** > **設定** > **配置** >常規> **常規**
   - **商店** > **設定** > **配置** >常規> **幣種設定**
   - **商店** > **設定** > **配置** >常規> **儲存電子郵件地址**

   當Commerce檢測到此類更改時，將顯示一條消息，通知您刷新快取。

- 維護商店（例如，添加或編輯類別、價格、產品和促銷定價規則）。

   當您執行上述任一任務時，清漆將自動清除。

- 維護原始碼。

   您應刷新快取，並定期刪除 `generated/code` 和 `generated/metadata` 的子菜單。 有關刷新快取的資訊，請參閱下一節。

## 將Commerce配置為清除清漆

在使用配置清漆主機後，Commerce清除清漆主機 [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) 的子菜單。

可以使用可選參數 `--http-cache-hosts` 參數，指定以逗號分隔的清漆主機和偵聽埠清單。 配置所有清漆主機，無論您有一個還是多個。 （不要將主機與空格字元分開。）

參數格式必須為 `<hostname or ip>:<listen port>`，在 `<listen port>` 如果是埠80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

然後，在刷新Commerce快取時可清除清漆主機(也稱為 *清洗* 快取)或使用命令行。

要使用Admin刷新快取，請按一下 **[!UICONTROL SYSTEM]** >工具> **快取管理**，然後按一下 **刷新Magento快取** 頁面頂部。 （也可以刷新單個快取類型。）

要使用命令行刷新快取，通常使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。
