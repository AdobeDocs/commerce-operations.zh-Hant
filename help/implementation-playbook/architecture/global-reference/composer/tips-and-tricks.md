---
title: 撰寫器提示與秘訣
description: 瞭解常見的撰寫器開發任務和快速解決問題的指引。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 撰寫器提示與秘訣

使用撰寫器開發Adobe Commerce模組時，您可能會遇到問題。 這些最佳實務說明一些常見的任務，可讓開發更輕鬆並幫助您快速解決問題。

>[!NOTE]
>
>這些准則主要適用於[全域參考架構(GRA)](../overview.md)專案。

## 加速撰寫器

安裝[https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo)，以加速非同步套件下載的Composer。

```bash
composer global require hirak/prestissimo
```

如果發生問題，請解除安裝`prestissimo`：

```bash
composer global remove hirak/prestissimo
```

## 解決模糊的版本設定問題

Composer有時會在套件版本中遭到鎖死。 您可能會看到與版本不相容的訊息，即使版本不相容亦然。 在偵錯相容性問題之前，請嘗試重設撰寫器：

1. 清除撰寫器快取。

   ```bash
   composer clearcache
   ```

1. 移除所有封裝的`composer.lock`檔案。

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. 重新安裝Composer套件。

   ```bash
   composer install
   ```

>[!TIP]
>
>這些步驟會將所有套件更新至最新可用版本。 從Git還原`composer.lock`檔案以復原這些升級。

## 檢查使用者端套件中可能的更新

1. 找出哪些套件可能已過時。

   ```bash
   composer outdated
   ```

1. 使用萬用字元和/或`--minor-only`選項進行篩選，以略過不向後相容的升級：

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## 檢視是否已安裝模組

檢視Git分支上所有已安裝套件的詳細資訊。

```bash
composer info
```

在切換Git分支之後和執行`composer info`之前執行`composer install`。 否則，Composer會顯示有關您簽出之先前分支的詳細資訊。

>[!TIP]
>
>若要篩選或搜尋，請使用下列指令之一。
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## 瞭解安裝（特定版本的）套件的原因

由於另一個套件有嚴格的相依性，有時Composer會安裝最新可用版本的套件。

檢視另一個套件中是否有嚴格的相依性。

```bash
composer why client/module-example
```

如果結果顯示中繼資料或其他非明確需要的套裝資料清單，請對該套裝資料執行命令：

```bash
composer why example/metapackage
```

## 瞭解未安裝套件的原因

有時，Composer不會安裝套件，因為它與其他套件衝突、其他套件取代它，或您尚未將其定義為相依性。

瞭解未安裝套件的原因。

```bash
composer why-not client/module-example
```

## 託管私人撰寫器存放庫

如果您需要私人Composer存放庫，請使用[Private Packagist](https://packagist.com/)或[JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/)。 請勿使用[Satis](https://github.com/composer/satis)。

- **私人套件商**&#x200B;是安全的，每年大約花費$600美元給三名管理員使用者，而且是託管的。

- **JFrog Artifactory**&#x200B;起始價格為每年$1,176美元。 它並不像Packagist那樣常用，但它支援的語言比PHP多。

- **Satis**&#x200B;沒有內建安全性、沒有自動化功能，而且需要額外的託管。 只有在您的時間也是免費的情況下，才有免費的空間。

## 版本設定套件

使用[Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html)，如Adobe Commerce [版本化結構描述](https://developer.adobe.com/commerce/php/development/versioning/)中所述。 不要再創造轉輪。

若為Adobe Commerce模組相依性，請遵循[模組版本相依性](https://developer.adobe.com/commerce/php/development/versioning/dependencies/)檔案。

請勿在`composer.json`檔案內使用版本定義。 請改用Git標籤來顯示版本。 請參閱[Composer版本和限制](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints)。

## 將傳入而不透過Composer的模組放在何處

為封存中的模組建立Git存放庫並自行託管。 每個Adobe Commerce模組都有`composer.json`檔案。 在Git中託管該檔案，並將其與Private Packagist同步之後，您就可以使用Composer進行安裝。

當您收到新版本的套件時，請將程式碼上傳到Git、標籤它，然後使用撰寫器安裝新版本。
