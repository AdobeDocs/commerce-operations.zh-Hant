---
title: 啟用或禁用模組
description: 按照以下步驟管理Adobe Commerce或Magento Open Source模組。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 啟用或禁用模組

此命令沒有先決條件。

## 模組狀態

使用以下命令列出已啟用和已禁用的模組：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

位置

* `--enabled` 列出所有已啟用的模組。
* `--disabled` 列出所有禁用的模組。
* `<module-list>` 是一個以空格分隔的模組清單，用於檢查狀態。 如果任何模組名稱包含特殊字元，請用單引號或雙引號將名稱括起來。

## 模組啟用、禁用

要啟用或禁用可用模組，請使用以下命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

位置

* `<module-list>` 是要啟用或禁用的以空格分隔的模組清單。 如果任何模組名稱包含特殊字元，請用單引號或雙引號將名稱括起來。
* `--all` 同時啟用或禁用所有模組。
* `-f` 或 `--force` 強制啟用或禁用模組（儘管存在依賴關係）。 在使用此選項之前，請參閱 [關於啟用和禁用模組](#about-enabling-and-disabling-modules)。
* `-c` 或 `--clear-static-content` 清洗 [生成的靜態視圖檔案](../../configuration/cli/static-view-file-deployment.md)。

   如果存在多個具有相同名稱的檔案且您未清除所有檔案，則無法清除靜態視圖檔案可能會導致問題。

   換句話說，因為 [靜態檔案回退](../../configuration/cli/static-view-file-deployment.md) 規則，如果您沒有清除靜態檔案，並且有多個檔案名為 `logo.svg` 不同，回退可能會導致顯示錯誤的檔案。

例如，要禁用 `Magento_Weee` 模組，輸入：

```bash
bin/magento module:disable Magento_Weee
```

有關啟用和禁用模組的重要資訊，請參見 [關於啟用和禁用模組](#about-enabling-and-disabling-modules)。

## 更新資料庫

如果啟用了一個或多個模組，請運行以下命令以更新資料庫：

```bash
bin/magento setup:upgrade
```

然後清除快取：

```bash
bin/magento cache:clean
```

## 關於啟用和禁用模組

Adobe Commerce和Magento Open Source使您能夠啟用或禁用當前可用的模組；換句話說，任何Adobe提供的模組或當前可用的任何第三方模組。

某些模組與其他模組有依賴關係，在這種情況下，您可能無法啟用或禁用某個模組，因為該模組與其他模組有依賴關係。

另外，可能 *衝突* 不能同時啟用的模組。

示例：

* 模組A取決於模組B。除非先禁用模組A，否則無法禁用模組B。

* 模組A取決於模組B，這兩個模組都被禁用。 必須先啟用模組B，然後才能啟用模組A。

* 模組A與模組B衝突。可以禁用模組A和模組B，也可以禁用其中一個模組，但 *不能* 同時啟用模組A和模組B。

* 依賴項在 `require` Adobe Commerce和Magento Open Source `composer.json` 檔案。 衝突在 `conflict` 模組中的欄位 `composer.json` 的子菜單。 我們使用這些資訊來構建依賴關係圖： `A->B` 表示模組A取決於模組B。

* A *依賴鏈* 是從一個模組到另一個模組的路徑。 例如，如果模組A依賴於模組B，而模組B依賴於模組C，則依賴鏈為 `A->B->C`。

如果嘗試啟用或禁用依賴於其他模組的模組，則相關性圖會顯示在錯誤消息中。

>[!NOTE]
>
>有可能是模組A `composer.json` 聲明與模組B衝突，但不反之。

*僅命令行：* 要強制啟用或禁用模組，請使用可選 `--force` 參數。

>[!NOTE]
>
>使用 `--force` 會禁用您的儲存並導致訪問管理員時出現問題。
