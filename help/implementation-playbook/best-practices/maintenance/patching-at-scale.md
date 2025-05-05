---
title: 大規模散發修補程式的最佳作法
description: 瞭解Adobe Commerce的集中修補如何協助您管理企業專案。
role: Developer
feature: Best Practices
badge: label="由Adobe高級技術架構師Tony Evers提供" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="托尼·埃弗斯撰寫"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 大規模散佈Adobe Commerce修補程式的最佳作法

如果您管理多個Adobe Commerce安裝，[修補](../../../upgrade/patches/apply.md)可能會是一個複雜的程式。 _集中修補_&#x200B;是企業的最佳作法。 它可協助您在所有Adobe Commerce安裝上套用正確的修補程式。 本主題說明如何針對所有型別的Adobe Commerce [修補程式](../../../upgrade/patches/overview.md)達成集中式修補程式散佈。

>[!NOTE]
>
>下列內容最初發佈在Adobe技術部落格上的[按比例分發Adobe Commerce修補程式](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20)文章中。 它已修改為專注於實作集中式修補策略的步驟和程式碼範例。 請參閱原始文章，以取得此處說明的不同修補程式型別的詳細資訊。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 策略

由於有許多不同型別的修補程式和套用修補程式的方法，您如何知道哪個修補程式會先套用？ 您擁有的修補程式越多，這些修補程式套用至相同檔案或相同程式碼行的機會就越大。 修補程式會依下列順序套用：

1. **安全性修補程式**&#x200B;是Adobe Commerce發行版本的靜態程式碼基底的一部分。
1. **Composer修補程式**&#x200B;透過`composer install`和`composer update`外掛程式，例如[cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches)。
1. 所有&#x200B;**必要的修補程式**&#x200B;包含在Commerce[&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html?lang=zh-Hant)封裝的雲端修補程式。
1. 已選取包含在[[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md)中的&#x200B;**品質修補程式**。
1. **自訂修補程式**&#x200B;以及`/m2-hotfixes`目錄中的Adobe Commerce支援修補程式，依修補程式名稱的字母順序排列。

   >[!IMPORTANT]
   >
   >您套用的修補程式越多，程式碼就越複雜。 複雜的程式碼會讓升級至新版Adobe commerce更加困難，並增加您的總擁有成本。

如果您負責維護Adobe Commerce的多個安裝，確保所有執行個體都安裝了相同的修補程式集，可能會相當困難。 每個安裝都有自己的Git存放庫、`/m2-hotfixes`目錄和`composer.json`檔案。 您唯一能保證的是，雲端使用者的&#x200B;**安全性修補程式**&#x200B;和&#x200B;**必要的修補程式**&#x200B;都作為主要Adobe Commerce版本的一部分安裝。

目前，此問題沒有單一集中式的解決方案，但Composer提供填補空白的方法。 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches)封裝可讓您[從相依性](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies)套用修補程式。 您可以建立可安裝所有修補程式的Composer套件，然後在所有專案中需要該套件。

涵蓋&#x200B;**安全性修補程式**、**必要的修補程式**&#x200B;及&#x200B;**Composer修補程式**，但品質修補程式及`/m2-hotfixes`目錄的內容呢？

## 套用高品質的修補程式和Hotfix

您可以使用`vendor/bin/magento-patches apply`命令，在雲端基礎結構和內部部署安裝上安裝高品質的修補程式。 您必須確定`vendor/bin/magento-patches apply`命令會在`composer install`作業之後執行。

>[!NOTE]
>
>在雲端基礎結構上，您也可以將品質修補程式列在您的專案的`.magento.env.yaml`檔案中，以安裝品質修補程式。 此處說明的範例需要使用`vendor/bin/magento-patches apply`命令。

您可以指定要在自訂Composer元件封裝的`composer.json`檔案中套用的修補程式，然後建立在`composer install`作業之後執行命令的外掛程式封裝。

總而言之，此集中式修補範例需要您建立兩個自訂撰寫器套裝程式：

- **元件封裝：** `centralized-patcher`

   - 定義品質修補程式清單及要安裝的`m2-hotfixes`
   - 需要`centralized-patcher-composer-plugin`套件，該套件會在`composer install`作業之後執行`vendor/bin/magento-patches apply`命令

- **外掛程式套件：** `centralized-patcher-composer-plugin`

   - 定義從`centralized-patcher`封裝讀取品質修補程式清單的`CentralizedPatcher` PHP類別
   - 執行`vendor/bin/magento-patches apply`命令以在`composer install`作業之後安裝品質修補程式清單

### `centralized-patcher`

您可以建立Composer元件套件(`centralized-patcher`)，以集中管理所有Adobe Commerce安裝中的所有品質修補程式和`/m2-hotfixes`。

元件套件必須：

- 在部署期間將`/m2-hotfixes`目錄的內容複製到所有安裝中。
- 定義要安裝的品質修補程式清單。
- 執行`vendor/bin/magento-patches`命令，在所有安裝中安裝相同的品質修補程式清單（使用[`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin)外掛程式套件做為相依性）。

若要建立`centralized-patcher`元件封裝：

1. 建立包含下列內容的`composer.json`檔案：

   >[!NOTE]
   >
   >下列範例中的`require`屬性顯示您稍後必須建立的[外掛程式套件](#centralized-patcher-composer-plugin)上的`require`相依性。

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. 在您的套件中建立`/m2-hotfixes`目錄，並將其新增至`composer.json`檔案中的`map`屬性。 `map`屬性包含要從此套件複製到要修補之目標專案根目錄的檔案。

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >`centralized-patcher`封裝將`/m2-hotfixes`目錄的內容複製到`composer install`上目標專案的m2-hotfix目錄中。  由於雲端部署指令碼會在`composer install`之後套用m2-hotfix，因此所有hotfix都是由部署機制安裝。

1. 定義要安裝在`quality-patches`屬性中的品質修補程式。

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


上述程式碼範例中的`quality-patches`屬性包含[完整修補程式清單](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)中的兩個修補程式，以為例。  這些品質修補程式會使用`vendor/bin/magento-patches apply`命令安裝在需要`centralized-patcher`套件的每個專案上。

您可以建立範例修補程式(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)以進行測試。

>[!NOTE]
>
>您應該將自己的修補程式連同您直接從Adobe Commerce支援收到的修補程式一起放在`m2-hotfixes`目錄中。

範例修補程式檔案(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)：

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

由於此範例使用內部部署方法來安裝品質修補程式，因此您必須確定`vendor/bin/magento-patches apply`命令會在`composer install`作業之後執行。 此外掛程式會在`composer install`作業之後觸發，該作業會執行`vendor/bin/magento-patches apply`命令。

若要建立`centralized-patcher-compose-plugin`元件封裝：

1. 建立包含下列內容的`composer.json`檔案：

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. 建立PHP檔案並定義`CentralizedPatcher`類別以從[`centralized-patcher`](#centralized-patcher)元件封裝讀取品質修補程式清單，並在每次`composer install`作業後立即安裝。

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>請參考[code-examples](#code-examples)，檢視此範例中說明的兩個封裝的實際運作情況。


## 如何處理專案專屬修補程式

您可能會遇到在所有專案中僅需要95%的修補程式，而少數修補程式僅套用至特定執行個體的情況。 套用修補的常規方法仍然有效。 您可以在`/m2-hotfixes`目錄中保留專案特定的修補程式，並為每個專案安裝品質修補程式。

如果您使用此方法，**不會**&#x200B;認可`/m2-hotfixes`目錄中任何已由`centralized-patcher`元件封裝複製到專案中的修補程式。 您可以將`/m2-hotfixes`新增至您的`.gitignore`檔案，以防止意外認可。 更新`.gitignore`檔案後，請記住，必須使用`git add –force`命令新增任何專案特定的`/m2-hotfixes`。

## 執行不同的Adobe Commerce版本

請確定您在`centralized-patcher`元件封裝中設定正確的相依性。 例如，您的特定套件版本可能需要Adobe Commerce 2.4.5-p2，此套件僅提供與Adobe Commerce 2.4.5-p2相容的修補程式。 您可以有此套件的其他版本與Adobe Commerce 2.4.4相容。

## 瞭解結果

就像在雲端基礎結構上使用Adobe Commerce一樣，本文假設您的部署程式使用`composer install`命令（而非`composer update`或`git pull`）將新程式碼部署到您的伺服器。 集中安裝修補程式的流程如下所示：

1. Composer安裝

   - 安裝Adobe Commerce，包括 — p1或 — p2安全性與功能修補程式
   - 結合集中式`/m2-hotfixes`，並透過專案特定的`/m2-hotfixes`支援修補程式以及支援修補程式
   - 套用隨`cweagans/composer-patches` Composer套件安裝的任何修補程式

1. `composer install`之後

   - Composer外掛程式會安裝集中式品質修補程式

1. 部署

   - 已根據`.magento.env.yaml`檔案安裝必要的修補程式和專案特定的品質修補程式(僅限雲端基礎結構專案上的Adobe Commerce)。
   - 自訂修補程式和`/m2-hotfixes`目錄中的支援修補程式會依修補程式名稱的字母順序安裝。

如此一來，您可以集中管理所有安裝的所有修補程式，更能保證Adobe Commerce存放區的安全性和穩定性。 請使用下列方法檢查修正程式狀態：

- [雲端基礎結構專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant#view-available-patches-and-status)
- [內部部署專案](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 程式碼範例

- [Magento Open Source中的集中式修補程式](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [在雲端基礎結構上的Adobe Commerce中集中修補程式](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [集中式修補程式撰寫器外掛程式](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [集中式修補程式元件](https://github.com/AntonEvers/centralized-patcher)
