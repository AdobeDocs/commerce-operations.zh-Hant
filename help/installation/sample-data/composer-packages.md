---
title: 下載示例資料合成器包
description: 按照以下步驟使用Composer PHP包管理器安裝Adobe Commerce和Magento Open Source示例資料。
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 下載示例資料合成器包

本節將討論如果您通過以下任何方式獲得Adobe Commerce或Magento Open Source軟體，如何安裝示例資料：

* 已從下載壓縮存檔 `https://magento.com/tech-resources/download`。

   如果從GitHub下載了存檔，則此方法不起作用，因為 `composer.json` 檔案不包含 `repo.magento.com` URL。

* 已用 `composer create-project`

您可以使用此方法獲取Adobe Commerce和Magento Open Source的示例資料，但必須使用相同的方法 [身份驗證密鑰](../prerequisites/authentication-keys.md) 安裝應用程式時的。

>[!NOTE]
>
>如果遇到錯誤，例如 `Could not find package...` 或 `...no matching package found...`，確保命令中沒有任何拼寫錯誤。 如果您仍然遇到錯誤，則可能無法訪問正確的Composer儲存庫，尤其是如果您使用的是Adobe Commerce。 聯繫人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 的雙曲餘切值。

可以在安裝應用程式之前或之後使用Composer安裝示例資料；但是可能 [其他任務](remove-or-update.md)。

如果您是派遣開發人員，請參閱 [通過克隆儲存庫進行安裝](git-repositories.md)。

>[!WARNING]
>
>如果應用程式已設定為，則不安裝示例資料 [生產模式](../../configuration/bootstrap/application-modes.md#production-mode)。 切換到 [開發者模式](../../configuration/bootstrap/application-modes.md#developer-mode) 。 在生產模式下安裝示例資料 [失敗](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-)。

要使用命令行安裝示例資料，請在 `<app_root>` 目錄：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>如果要安裝示例資料 _後_ 安裝應用程式時，還必須運行以下命令以更新 `<app_root>` 目錄：

```bash
bin/magento setup:upgrade
```

您必須 [驗證](../prerequisites/authentication-keys.md) 完成操作。

## 驗證錯誤

可能顯示以下驗證錯誤：

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

如果顯示錯誤，請更改到應用程式安裝目錄並運行 `composer update`，提示您 [身份驗證密鑰](../prerequisites/authentication-keys.md)。

## 完成示例資料安裝

{{$include /help/_includes/sample-data-complete.md}}
