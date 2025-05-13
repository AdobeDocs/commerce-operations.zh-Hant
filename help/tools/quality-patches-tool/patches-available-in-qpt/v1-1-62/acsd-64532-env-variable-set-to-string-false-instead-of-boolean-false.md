---
title: ACSD-64532：設為*false*的環境變數會被視為字串*false*，而非布林值*FALSE*
description: 套用ACSD-64532修補程式以修正Adobe Commerce的問題，也就是將設為*false*的「ENV」變數視為字串*false*，而非「BOOLEAN」*FALSE*。
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532：設為「false」的環境變數會被視為字串「false」，而非布林值FALSE

ACSD-64532修補程式修正將`ENV`變數設為&#x200B;*false*&#x200B;視為字串&#x200B;*false*&#x200B;而非`BOOLEAN` *FALSE*&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 修補程式ID為ACSD-64532。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**
Adobe Commerce （所有部署方法） 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設為&#x200B;*false*&#x200B;的`ENV`變數會被視為字串&#x200B;*false*，而非`BOOLEAN` *FALSE*。

<u>要再現的步驟</u>：
1. 將值為&#x200B;*false*&#x200B;的`env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK`新增至雲端基礎結構上Adobe Commerce的環境變數。
1. 等待重新部署。
1. 執行指令碼檢查值：

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>預期結果</u>：
`$configParsedValue` （方法`isUseApplicationLock()`的結果）必須傳回負值，才能在方法`\Magento\Indexer\Model\Mview\View\State::getStatus()`內正確解譯。

<u>實際結果</u>：
`$configParsedValue`具有&#x200B;*`string(5) false`*&#x200B;的值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：
* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
