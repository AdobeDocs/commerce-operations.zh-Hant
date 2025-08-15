---
title: 使用清漆清除快取
description: 瞭解快取清除如何與Varnish搭配運作，以及如何將其用作Adobe Commerce應用程式的網頁快取加速器。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 使用清漆清除快取

本主題說明使用Varnish做為Adobe Commerce網頁快取加速器的基本概念。

## 清漆清除

根據[Varnish檔案](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)，「當您從快取中挑選物件並捨棄它及其變體時，就會發生&#x200B;*清除*。」 清漆清除類似於快取清除命令(或按一下[管理員]中的[清除Magento快取] **。**

事實上，當您清除、排清或重新整理Commerce快取時，「清漆」也會清除。

安裝並設定Varnish以搭配Commerce使用後，下列動作可能會導致Varnish清除：

- 維護網站。

  例如，您在管理員中執行的任何操作：

   - **商店** > **設定** > **設定** >一般> **一般**
   - **商店** > **設定** > **設定** >一般> **貨幣設定**
   - **商店** > **設定** > **設定** >一般> **商店電子郵件地址**

  當Commerce偵測到這類變更時，會顯示一則訊息，通知您重新整理快取。

- 維護商店（例如，新增或編輯類別、價格、產品和促銷定價規則）。

  當您執行任何這些工作時，會自動清除清漆。

- 維護原始程式碼。

  您應該重新整理快取，並定期刪除`generated/code`和`generated/metadata`目錄中的所有專案。 如需重新整理快取的詳細資訊，請參閱下一節。

## 設定Commerce以清除清漆

使用[`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset)命令設定Varnish主機後，Commerce會清除清漆主機。

您可以使用選用的引數`--http-cache-hosts`引數，指定以逗號分隔的Varnish主機和監聽連線埠清單。 設定所有Varnish主機，無論您有一台或多台。 （請勿以空格字元分隔主機。）

引數格式必須是`<hostname or ip>:<listen port>`，若是連線埠80，則可以省略`<listen port>`。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

當您在管理員中重新整理Commerce快取（也稱為&#x200B;*清除*&#x200B;快取）或使用命令列時，就可以清除Varnish主機。

若要使用Admin重新整理快取，請按一下[工具] > [快取管理] **[!UICONTROL SYSTEM]** **，然後按一下頁面頂端的[排清Magento快取]**。 ****（您也可以重新整理個別快取型別。）

若要使用命令列重新整理快取，您通常使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令作為[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
