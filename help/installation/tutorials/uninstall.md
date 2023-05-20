---
title: 卸載或重新安裝Adobe Commerce
description: 按照以下步驟卸載並重新安裝Adobe Commerce和Magento Open Source的本地安裝。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 卸載或重新安裝Adobe Commerce

在使用這些命令之前，必須 [安裝應用程式](../tutorials/install.md)。

## 更新應用程式

要更新應用程式，請執行以下操作：

* 如果從存檔檔案安裝軟體，或者使用「composer-create-project」，請參見 [升級指南](../../upgrade/overview.md)。
* 如果您是特派開發人員(即 `git clone`)，請參閱 [更新應用程式](../../upgrade/developer/git-installs.md)。

## 重新安裝應用程式

從命令行重新安裝應用程式的方式取決於您的角色：

* 如果從存檔檔案安裝軟體，或者使用了「composer-create-project」，請參見 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)。
* 如果您是開發人員(即，您開始使用 `git clone`)，請參閱 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)。

## 卸載應用程式

卸載應用程式將刪除和還原資料庫，刪除部署配置，並清除下面的目錄 `var`。

要卸載應用程式，請輸入以下命令：

```bash
bin/magento setup:uninstall
```

顯示以下消息以確認卸載成功：

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## （可選）保留生成的檔案

預設情況下， `bin/magento setup:upgrade` 清除已編譯的代碼和快取。 通常，您 `bin/magento setup:upgrade` 要更新元件，並且每個元件可能需要不同的編譯類。

但是，在某些情況下（特別是部署到生產環境），您可能希望避免清除已編譯的代碼，因為這可能需要一些時間。 （快取仍被清除。） 更新資料庫架構和資料 *無* 清除編譯代碼，輸入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>可選 `--keep-generated` 選項應在有限情況下由有經驗的系統整合商使用 *僅*。 此選項應 *從不* 用於開發環境。 不正確使用此可選參數可能會導致代碼執行過程中出錯。

## 安裝應用程式

* [使用命令行進行安裝](../advanced.md)
