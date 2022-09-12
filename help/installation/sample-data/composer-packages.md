---
title: 下載範例資料撰寫器套件
description: 請依照下列步驟，使用撰寫器PHP套件管理器來安裝Adobe Commerce和Magento Open Source範例資料。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# 下載範例資料撰寫器套件

本節探討如果您取得Adobe Commerce或Magento Open Source軟體，透過下列任一方式，即可安裝範例資料：

* 從下載壓縮的封存 `https://magento.com/tech-resources/download`.

   如果您從GitHub下載封存，此方法無法運作，因為 `composer.json` 檔案不包含 `repo.magento.com` URL。

* 已使用 `composer create-project`

您可以使用此方法來取得Adobe Commerce和Magento Open Source的範例資料，但您必須使用相同的 [驗證金鑰](../prerequisites/authentication-keys.md) 用於安裝應用程式。

>[!NOTE]
>
>如果您遇到錯誤，例如 `Could not find package...` 或 `...no matching package found...`，請確定您的命令中沒有任何錯字。 如果您仍遇到錯誤，您可能無法存取正確的撰寫器存放庫，尤其是如果您使用的是Adobe Commerce。 連絡人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 來幫忙。

您可以在安裝應用程式之前或之後，使用撰寫器來安裝範例資料；然而， [其他任務](remove-or-update.md).

如果您是貢獻開發人員，請參閱 [通過克隆儲存庫進行安裝](git-repositories.md).

>[!WARNING]
>
>如果您的應用程式設定為 [生產模式](../../configuration/bootstrap/application-modes.md#production-mode). 切換至 [開發人員模式](../../configuration/bootstrap/application-modes.md#developer-mode) 第一個。 在生產模式中安裝範例資料 [失敗](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

要使用命令行安裝示例資料，請在 `<app_root>` 目錄：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>如果要安裝示例資料 _after_ 安裝應用程式時，還必須運行以下命令以更新 `<app_root>` 目錄：

```bash
bin/magento setup:upgrade
```

您必須 [驗證](../prerequisites/authentication-keys.md) 以完成動作。

## 驗證錯誤

可能會顯示下列驗證錯誤：

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

如果顯示錯誤，請更改到應用程式安裝目錄並運行 `composer update`，提示您 [驗證金鑰](../prerequisites/authentication-keys.md).

## 完成範例資料安裝

{{$include /help/_includes/sample-data-complete.md}}
