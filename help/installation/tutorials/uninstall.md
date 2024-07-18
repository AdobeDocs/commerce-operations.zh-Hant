---
title: 解除安裝或重新安裝Adobe Commerce
description: 請依照下列步驟，解除安裝並重新安裝Adobe Commerce的內部部署。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 解除安裝或重新安裝Adobe Commerce

使用這些命令之前，您必須[安裝應用程式](../tutorials/install.md)。

## 更新應用程式

若要更新應用程式，請執行下列動作：

* 若您是從封存安裝軟體，或使用&#39;composer-create-project&#39;，請參閱[升級指南](../../upgrade/overview.md)。
* 如果您是參與開發人員（也就是您使用了`git clone`），請參閱[更新應用程式](../../upgrade/developer/git-installs.md)。

## 重新安裝應用程式

從命令列重新安裝應用程式的方式取決於您的角色：

* 如果您是從封存安裝軟體，或使用&#39;composer-create-project&#39;，請參閱[更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)。
* 如果您是參與開發人員（亦即您已開始使用`git clone`），請參閱[更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)。

## 解除安裝應用程式

解除安裝應用程式會刪除並還原資料庫、移除部署設定，以及清除`var`下的目錄。

若要解除安裝應用程式，請輸入下列命令：

```bash
bin/magento setup:uninstall
```

系統會顯示下列訊息，確認解除安裝成功：

```
[SUCCESS]: Magento uninstallation complete.
```

## 可選擇保留產生的檔案

依預設，`bin/magento setup:upgrade`會清除編譯的程式碼和快取。 一般而言，您會使用`bin/magento setup:upgrade`來更新元件，而每個元件可能需要不同的編譯類別。

但是，在某些情況下（特別是部署到生產環境），您可能希望避免清除編譯的程式碼，因為可能需要一些時間。 （快取仍會清除。） 若要更新資料庫結構描述和資料&#x200B;*，而不需要*&#x200B;清除編譯的程式碼，請輸入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>選擇性`--keep-generated`選項只應在有限的情況下由經驗豐富的系統整合器&#x200B;*使用*。 此選項應&#x200B;*永遠不要在開發環境中使用*。 不當使用此選用引數，可能會在程式碼執行期間導致錯誤。

## 安裝應用程式

* [使用命令列安裝](../advanced.md)
