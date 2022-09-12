---
title: 解除安裝或重新安裝Adobe Commerce
description: 請依照下列步驟，解除安裝並重新安裝Adobe Commerce和Magento Open Source的內部部署安裝。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# 解除安裝或重新安裝Adobe Commerce

使用這些命令之前，您必須 [安裝應用程式](../tutorials/install.md).

## 更新應用程式

要更新應用程式，請執行以下操作：

* 如果您是從封存安裝軟體，或使用「composer-create-project」，請參閱 [升級指南](../../upgrade/overview.md).
* 如果您是貢獻開發人員(即您使用 `git clone`)，請參閱 [更新應用程式](../../upgrade/developer/git-installs.md).

## 重新安裝應用程式

從命令行重新安裝應用程式的方式取決於您的角色：

* 如果您是從封存安裝軟體，或使用「composer-create-project」，請參閱 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 如果您是貢獻開發人員(即您開始使用 `git clone`)，請參閱 [更新安裝依賴項](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 解除安裝應用程式

卸載應用程式會丟棄和還原資料庫，刪除部署配置，並清除 `var`.

要卸載應用程式，請輸入以下命令：

```bash
bin/magento setup:uninstall
```

將顯示以下消息以確認卸載是否成功：

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## （可選）保留生成的檔案

依預設， `bin/magento setup:upgrade` 會清除已編譯的程式碼和快取。 通常，您會使用 `bin/magento setup:upgrade` 要更新元件，每個元件可能需要不同的編譯類。

但在某些情況下（尤其是部署至生產環境），您可能會希望避免清除已編譯的程式碼，因為可能需要一些時間。 ( [快取](https://glossary.magento.com/cache) 仍清空。) 若要更新 [資料庫模式](https://glossary.magento.com/database-schema) 和資料 *無* 清除編譯的代碼，請輸入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>選填 `--keep-generated` 有經驗的系統整合商應在有限情況下使用選項 *僅限*. 此選項應 *從不* 用於開發環境。 若使用此選用參數不當，可能會在程式碼執行期間造成錯誤。

## 安裝應用程式

* [使用命令列安裝](../advanced.md)
