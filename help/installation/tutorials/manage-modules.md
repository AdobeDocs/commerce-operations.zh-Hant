---
title: 啟用或禁用模組
description: 請依照下列步驟管理Adobe Commerce或Magento Open Source模組。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# 啟用或禁用模組

此命令沒有先決條件。

## 模組狀態

使用以下命令列出已啟用和禁用的模組：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

其中

* `--enabled` 列出所有已啟用的模組。
* `--disabled` 列出所有禁用的模組。
* `<module-list>` 是以空格分隔的模組清單，用於檢查狀態。 如果有 [模組](https://glossary.magento.com/module) name包含特殊字元，請以單引號或雙引號將名稱括住。

## 模組啟用，禁用

要啟用或禁用可用模組，請使用以下命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

其中

* `<module-list>` 是要啟用或停用的以空格分隔的模組清單。 如果有 [模組](https://glossary.magento.com/module) name包含特殊字元，請以單引號或雙引號將名稱括住。
* `--all` 啟用或禁用所有模組。
* `-f` 或 `--force` 強制啟用或停用模組（無論相依性如何）。 使用此選項之前，請參閱 [關於啟用和禁用模組](#about-enabling-and-disabling-modules).
* `-c` 或 `--clear-static-content` 清除 [生成的靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md).

   如果有多個檔案具有相同名稱，且您未清除所有檔案，若無法清除靜態檢視檔案，可能會導致問題。

   換句話說，由於 [靜態檔備援](../../configuration/cli/static-view-file-deployment.md) 規則，如果您未清除靜態檔案，且有多個檔案名為 `logo.svg` 不同，後援可能會顯示錯誤的檔案。

例如，若要停用 `Magento_Weee` 模組，輸入：

```bash
bin/magento module:disable Magento_Weee
```

有關啟用和禁用模組的重要資訊，請參見 [關於啟用和禁用模組](#about-enabling-and-disabling-modules).

## 更新資料庫

如果啟用一個或多個模組，請運行以下命令以更新資料庫：

```bash
bin/magento setup:upgrade
```

然後清除快取：

```bash
bin/magento cache:clean
```

## 關於啟用和禁用模組

Adobe Commerce和Magento Open Source可讓您啟用或停用目前可用的模組；換言之，任何Adobe提供的模組或目前可用的任何協力廠商模組。

某些模組對其他模組具有依賴性，在這種情況下，您可能無法啟用或禁用模組，因為該模組對其他模組具有依賴性。

此外， *衝突* 無法同時啟用的模組。

範例：

* 模組A取決於模組B。除非您先停用模組A，否則無法停用模組B。

* 模組A取決於模組B，兩者皆已停用。 必須先啟用模組B，才能啟用模組A。

* 模組A與模組B衝突。您可以停用模組A和模組B，或者您可以停用其中一個模組，但您 *不能* 同時啟用模組A和模組B。

* 相依性在 `require` 欄位於Adobe Commerce和Magento Open Source `composer.json` 檔案。 衝突在 `conflict` 模組中的欄位 `composer.json` 檔案。 我們會利用這些資訊來建立相依圖： `A->B` 表示模組A取決於模組B。

* A *依賴鏈* 是從模組到另一個模組的路徑。 例如，如果模組A依賴模組B，而模組B依賴模組C，則相依鏈為 `A->B->C`.

如果您嘗試啟用或停用依賴其他模組的模組，相依性圖表會顯示在錯誤訊息中。

>[!NOTE]
>
>A模組可能 `composer.json` 聲明與模組B衝突，但不是相反。

*僅命令行：* 若要強制啟用或停用模組（無論其相依性為何），請使用選用 `--force` 引數。

>[!NOTE]
>
>使用 `--force` 可停用您的商店，並造成存取管理員時發生問題。
