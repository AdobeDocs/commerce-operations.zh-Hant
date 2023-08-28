---
title: 大規模散發修補程式的最佳作法
description: 瞭解Adobe Commerce的集中修補如何協助您管理企業專案。
role: Developer
feature: Best Practices
badge: label="由Adobe高級技術架構師Anton Evers提供" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="安東·埃弗斯撰寫"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# 大規模散佈Adobe Commerce修補程式的最佳作法

如果您管理多個Adobe Commerce安裝， [修補](../../../upgrade/patches/apply.md) 可能是一個複雜的過程。 _集中修補_ 是的重要部分 [全球參考架構](../../architecture/global-reference/overview.md) 也是企業的最佳作法。 它可協助您在所有Adobe Commerce安裝上套用正確的修補程式。 本主題說明如何針對所有型別的Adobe Commerce達成集中式修補程式散佈 [修補程式](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>下列內容最初發佈於 [大規模散佈Adobe Commerce修補程式](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) 在Adobe技術部落格上發文。 它已修改為專注於實作集中式修補策略的步驟和程式碼範例。 請參閱原始文章，以取得此處說明的不同修補程式型別的詳細資訊。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 策略

由於有許多不同型別的修補程式和套用修補程式的方法，您如何知道哪個修補程式會先套用？ 您擁有的修補程式越多，這些修補程式套用至相同檔案或相同程式碼行的機會就越大。 修補程式會依下列順序套用：

1. **安全性修補程式** 是Adobe Commerce發行版本的靜態程式碼庫的一部分。
1. **Composer修補程式** 到 `composer install` 和 `composer update` 外掛程式，例如 [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. 全部 **必要的修補程式** 包含在 [Commerce雲端修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) 封裝。
1. 已選取 **品質修補程式** 包含在 [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **自訂修補程式** 和Adobe Commerce支援修補程式(在 `/m2-hotfixes` 目錄，依修補程式名稱的字母順序。

   >[!IMPORTANT]
   >
   >您套用的修補程式越多，程式碼就越複雜。 複雜的程式碼會讓升級至新版Adobe commerce更加困難，並增加您的總擁有成本。

如果您負責維護Adobe Commerce的多個安裝，確保所有執行個體都安裝了相同的修補程式集，可能會相當困難。 每個安裝都有自己的Git存放庫， `/m2-hotfixes` 目錄，和 `composer.json` 檔案。 您唯一能保證的是 **安全性修補程式** 和 **必要的修補程式** 適用於雲端的使用者都會當作主要Adobe Commerce版本的一部分安裝。

目前，此問題沒有單一集中式的解決方案，但Composer提供填補空白的方法。 此 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) 套件可讓您 [從相依性套用修補程式](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). 您可以建立可安裝所有修補程式的Composer套件，然後在所有專案中需要該套件。

涵蓋 **安全性修補程式**， **必要的修補程式**、和 **Composer修補程式**，但是品質修補程式和內容呢？ `/m2-hotfixes` 目錄？

## 套用高品質的修補程式和Hotfix

您可以使用在雲端基礎結構和內部部署安裝上安裝品質修補程式 `vendor/bin/magento-patches apply` 命令。 您必須確保 `vendor/bin/magento-patches apply` 命令執行於 `composer install` 操作。

>[!NOTE]
>
>在雲端基礎結構上，您也可以透過在專案的 `.magento.env.yaml` 檔案。 此處說明的範例需要使用 `vendor/bin/magento-patches apply` 命令。

您可以指定要套用到的修補程式 `composer.json` 自訂Composer元件套件的檔案，然後建立外掛程式套件以在之後執行命令 `composer install` 操作。

總而言之，此集中式修補範例需要您建立兩個自訂撰寫器套裝程式：

- **元件封裝：** `centralized-patcher`

   - 定義品質修補程式的清單，以及 `m2-hotfixes` 以安裝
   - 需要 `centralized-patcher-composer-plugin` 封裝，會執行 `vendor/bin/magento-patches apply` 命令晚於 `composer install` 操作

- **外掛程式套件：** `centralized-patcher-composer-plugin`

   - 定義 `CentralizedPatcher` 從讀取品質修補程式清單的PHP類別 `centralized-patcher` 封裝
   - 執行 `vendor/bin/magento-patches apply` 之後安裝品質修補程式清單的命令 `composer install` 操作

### `centralized-patcher`

您可以建立Composer元件套件(`centralized-patcher`)集中管理所有品質的修補程式，以及 `/m2-hotfixes` 所有Adobe Commerce安裝中的事件。

元件套件必須：

- 複製 `/m2-hotfixes` 在部署期間將目錄移至您的所有安裝中。
- 定義要安裝的品質修補程式清單。
- 執行 `vendor/bin/magento-patches` 命令在所有安裝中安裝相同的品質修補程式清單(使用 [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) 外掛程式套件做為相依性)。

若要建立 `centralized-patcher` 元件封裝：

1. 建立 `composer.json` 包含下列內容的檔案：

   >[!NOTE]
   >
   >此 `require` 屬性在下列範例中顯示 `require` 相依於 [外掛程式套件](#centralized-patcher-composer-plugin) 您稍後必須建立此範例。

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

1. 建立 `/m2-hotfixes` 目錄在您的套件中，並將它新增至 `map` 屬性位於 `composer.json` 檔案。 此 `map` attribute包含要從此套件複製到要修正之目標專案根目錄的檔案。

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
   >此 `centralized-patcher` 套件會複製 `/m2-hotfixes` 目錄至上的目標專案的m2-hotfixes目錄 `composer install`.  由於雲端部署指令碼會在之後套用m2-hotfix `composer install`，所有Hotfix都是由部署機制安裝。

1. 定義要安裝在中的品質修補程式 `quality-patches` 屬性。

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


此 `quality-patches` 屬性在前面的程式碼範例中，包含兩個來自 [完整修補程式清單](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 以為例。  這些品質修補程式會安裝在每個需要 `centralized-patcher` 封裝使用 `vendor/bin/magento-patches apply` 命令。

如需測試，您可以建立範例修補程式(`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`)。

>[!NOTE]
>
>您應該將自己的修補程式放在 `m2-hotfixes` 目錄，以及您直接從Adobe Commerce支援接收的修補程式。

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

由於此範例使用內部部署方法來安裝高品質的修補程式，因此您必須確定 `vendor/bin/magento-patches apply` 命令執行於 `composer install` 操作。 此外掛程式於以下時間觸發： `composer install` 作業，執行 `vendor/bin/magento-patches apply` 命令。

若要建立 `centralized-patcher-compose-plugin` 元件封裝：

1. 建立 `composer.json` 包含下列內容的檔案：

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

1. 建立PHP檔案並定義 `CentralizedPatcher` 類別以讀取品質修補程式清單 [`centralized-patcher`](#centralized-patcher) 元件封裝並在每隔 `composer install` 作業。

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
>請參閱 [程式碼範例](#code-examples) 以實際檢視此範例中說明的兩個套件。


## 如何處理專案專屬修補程式

您可能會遇到在所有專案中僅需要95%的修補程式，而少數修補程式僅套用至特定執行個體的情況。 套用修補的常規方法仍然有效。 您可以保留專案特定的修補程式 `/m2-hotfixes` 每個專案的目錄及安裝品質修補程式。

如果您使用此方法， **不要** 認可中的任何修補程式 `/m2-hotfixes` 已由複製到您專案中的目錄 `centralized-patcher` 元件封裝。 您可以透過新增來防止意外認可 `/m2-hotfixes` 至您的 `.gitignore` 檔案。 更新後 `.gitignore` 檔案中，請記住，任何專案專屬的 `/m2-hotfixes` 必須使用新增 `git add –force` 命令。

## 執行不同的Adobe Commerce版本

請確定您在中設定正確的相依性 `centralized-patcher` 元件封裝。 例如，您的特定套件版本可能需要Adobe Commerce 2.4.5-p2，此套件僅提供與Adobe Commerce 2.4.5-p2相容的修補程式。 您可以有此套件的其他版本與Adobe Commerce 2.4.4相容。

## 瞭解結果

就像在雲端基礎結構上使用Adobe Commerce一樣，本文假設您的部署程式使用 `composer install` 命令而非 `composer update` 或 `git pull` 將新程式碼部署到伺服器。 集中安裝修補程式的流程如下所示：

1. Composer安裝

   - 安裝Adobe Commerce，包括 — p1或 — p2安全性與功能修補程式
   - 結合集中式 `/m2-hotfixes` 並支援專案專屬的修補程式 `/m2-hotfixes` 和支援修補程式
   - 套用隨附安裝的任何修補程式 `cweagans/composer-patches` Composer套件

1. 晚於 `composer install`

   - Composer外掛程式會安裝集中式品質修補程式

1. 部署

   - 所需的修補程式和專案特定的品質修補程式是根據 `.magento.env.yaml` 檔案(僅限雲端基礎結構專案上的Adobe Commerce)。
   - 自訂修補程式及支援修補程式，來自 `/m2-hotfixes` 目錄會依修補程式名稱的字母順序進行安裝。

如此一來，您可以集中管理所有安裝的所有修補程式，更能保證Adobe Commerce存放區的安全性和穩定性。 請使用下列方法檢查修正程式狀態：

- [雲端基礎結構專案](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [內部部署專案](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## 程式碼範例

- [Magento Open Source集中修補程式](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [雲端基礎結構上的Adobe Commerce集中式修補程式](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [集中式修補程式撰寫器外掛程式](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [集中式修補程式元件](https://github.com/AntonEvers/centralized-patcher)
