---
title: 啟用或停用模組
description: 請依照下列步驟管理Adobe Commerce模組。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# 啟用或停用模組

這個命令沒有先決條件。

## 模組狀態

使用下列命令列出已啟用和已停用的模組：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

位置

* `--enabled`列出所有已啟用的模組。
* `--disabled`列出所有已停用的模組。
* `<module-list>`是以空格分隔的模組清單，用於檢查狀態。 如果任何模組名稱包含特殊字元，請以單引號或雙引號括住名稱。

>[!NOTE]
>
>您無法直接在雲端專案上啟用或停用模組。 您必須在本機執行這些命令，然後將變更推送到環境的`app/etc/config.php`檔案。 請參閱[Pro專案工作流程：部署工作流程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=zh-Hant#deployment-workflow)。

## 啟用、停用模組

若要啟用或停用可用的模組，請使用下列命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

位置

* `<module-list>`是以空格分隔的模組清單，可啟用或停用。 如果任何模組名稱包含特殊字元，請以單引號或雙引號括住名稱。
* `--all`以同時啟用或停用所有模組。
* `-f`或`--force`強制啟用或停用模組，無論相依性為何。 使用此選項之前，請參閱[關於啟用和停用模組](#about-enabling-and-disabling-modules)。
* `-c`或`--clear-static-content`會清除[產生的靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md)。

  如果存在多個同名檔案，但未全部清除，則無法清除靜態檢視檔案可能會導致問題。

  換言之，由於[靜態檔案遞補](../../configuration/cli/static-view-file-deployment.md)規則，如果您不清除靜態檔案，且有多個名為`logo.svg`的檔案不同，則遞補可能會導致顯示錯誤的檔案。

例如，若要停用`Magento_Weee`模組，請輸入：

```bash
bin/magento module:disable Magento_Weee
```

如需有關啟用和停用模組的重要資訊，請參閱[關於啟用和停用模組](#about-enabling-and-disabling-modules)。

## 更新資料庫

如果您啟用一或多個模組，請執行以下命令來更新資料庫：

```bash
bin/magento setup:upgrade
```

然後清除快取：

```bash
bin/magento cache:clean
```

## 關於啟用和停用模組

Adobe Commerce可讓您啟用或停用目前可用的模組；換言之，任何Adobe提供的模組或任何目前可用的協力廠商模組。

某些模組具有對其他模組的相依性，在這種情況下，您可能無法啟用或停用模組，因為它具有對其他模組的相依性。

此外，可能有&#x200B;*個衝突的*&#x200B;模組無法同時啟用。

範例：

* 模組A相依於模組B。除非先停用模組A，否則無法停用模組B。

* 模組A相依於模組B，兩者皆已停用。 您必須先啟用模組B，才能啟用模組A。

* 模組A與模組B衝突。您可以停用模組A和模組B，也可以停用任一模組，但您&#x200B;*無法*&#x200B;同時啟用模組A和模組B。

* 相依性在每個模組的Adobe Commerce `composer.json`檔案的`require`欄位中宣告。 在模組`composer.json`檔案的`conflict`欄位中宣告衝突。 我們使用該資訊來建置相依性圖表： `A->B`表示模組A相依於模組B。

* *相依性鏈結*&#x200B;是從模組到另一個模組的路徑。 例如，如果模組A相依於模組B，而模組B相依於模組C，則相依性鏈結為`A->B->C`。

如果您嘗試啟用或停用相依於其他模組的模組，相依性圖表會顯示在錯誤訊息中。

>[!NOTE]
>
>模組A的`composer.json`可能會宣告與模組B衝突，但反之則不然。

*僅限命令列：*&#x200B;若要強制啟用或停用模組（不論其相依性為何），請使用選用的`--force`引數。

>[!NOTE]
>
>使用`--force`可以停用您的存放區，並導致存取管理員時發生問題。
