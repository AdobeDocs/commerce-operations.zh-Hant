---
title: 下載範例資料撰寫器套件
description: 請依照下列步驟，使用Composer PHP Package Manager安裝Adobe Commerce範例資料。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 下載範例資料撰寫器套件

本節探討如何安裝範例資料(若您透過下列任一方式取得Adobe Commerce軟體)：

* 已從`https://magento.com/tech-resources/download`下載壓縮封存。

  如果您從GitHub下載封存，此方法將無法運作，因為`composer.json`檔案不包含`repo.magento.com` URL。

* 已使用`composer create-project`

您可以使用這個方法取得Adobe Commerce的範例資料，但必須使用安裝應用程式時所用的相同[驗證金鑰](../prerequisites/authentication-keys.md)。

>[!NOTE]
>
>如果您遇到錯誤（例如`Could not find package...`或`...no matching package found...`），請確定您的命令中沒有任何拼寫錯誤。 如果您仍然遇到錯誤，則可能無法存取正確的Composer存放庫，尤其是當您使用Adobe Commerce時。 請連絡[Adobe Commerce支援](https://support.magento.com/hc/en-us)尋求協助。

您可以使用Composer在安裝應用程式之前或之後安裝範例資料；但是，可能有[個其他工作](remove-or-update.md)。

如果您是參與開發人員，請參閱[複製存放庫以安裝](git-repositories.md)。

>[!WARNING]
>
>如果您的應用程式設定為[生產模式](../../configuration/bootstrap/application-modes.md#production-mode)，請勿安裝範例資料。 請先切換至[開發人員模式](../../configuration/bootstrap/application-modes.md#developer-mode)。 在生產模式[中安裝範例資料失敗](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-)。

若要使用命令列安裝範例資料，請在`<app_root>`目錄中輸入下列命令作為檔案系統擁有者：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>如果要在安裝應用程式&#x200B;_之後安裝範例資料_，您也必須執行下列命令來更新`<app_root>`目錄中的資料庫和結構描述：

```bash
bin/magento setup:upgrade
```

您必須[驗證](../prerequisites/authentication-keys.md)才能完成動作。

## 驗證錯誤

可能會顯示下列驗證錯誤：

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

如果顯示錯誤，請變更至您的應用程式安裝目錄，並執行`composer update`，這會提示您輸入[驗證金鑰](../prerequisites/authentication-keys.md)。

## 完成範例資料安裝

{{$include /help/_includes/sample-data-complete.md}}
