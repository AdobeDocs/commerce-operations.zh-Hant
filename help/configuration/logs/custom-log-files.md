---
title: 寫入自定義日誌檔案
description: 學習設定自定義日誌檔案。
feature: Configuration, Logs
badge: label="由Atwix提供" type="Informity" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 寫入自定義日誌檔案

的 `Magento\Framework\Logger` 模組包含以下處理程式類：

| 類 | 日誌檔案 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

你可以在 `lib/internal/Magento/Framework/Logger/Handler` 的子菜單。

您可以使用以下方法之一登錄到自定義檔案：

- 在 `di.xml`
- 在自定義記錄器處理程式類中設定自定義檔案

## 在 `di.xml`

此示例說明如何使用 [虛擬類型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 記錄 `debug` 消息到自定義日誌檔案，而不是標準 `/var/log/debug.log`。

1. 在 `di.xml` 檔案，將自定義日誌檔案定義為 [虛擬類型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types)。

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   的 `name` 值 `Magento\Payment\Model\Method\MyCustomDebug` 必須是唯一的。

1. 在另一個中定義處理程式 [虛擬類型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 具有獨特 `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 插入 `MyCustomLogger` [虛擬類型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 的 `Magento\Payment\Model\Method\Logger` 對象：

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 虛擬類 `Magento\Payment\Model\Method\MyCustomDebug` 注入 `debug` 處理程式 `$logger` 屬性 `Magento\Payment\Model\Method\Logger` 類。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

異常消息已記錄到 `/var/log/payment.log` 的子菜單。

## 在記錄器處理程式類中設定自定義日誌檔案

此示例說明如何使用自定義記錄器處理程式類來記錄 `error` 消息到特定日誌檔案。

1. 建立記錄資料的類。 在本示例中，類在 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`。

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. 將此類的處理程式定義為 [虛擬類型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 在 `di.xml` 的子菜單。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` 是唯一標識符。

1. 在 `type` 定義，指定注入自定義記錄器處理程式的類名。 使用上一步中的虛擬類型名稱作為此類型的參數。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   原始碼 `Vendor\ModuleName\Observer\MyObserver` 類：

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. 類 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 注入 `error` 處理程式 `$logger` 屬性 `Vendor\ModuleName\Observer\MyObserver`。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

異常消息記錄在 `/var/log/my_custom_logger/error.log` 的子菜單。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
