---
title: 記錄器介面
description: 瞭解如何在Adobe Commerce中使用記錄器介面進行自訂記錄。 探索PSR-3實作和記錄函式。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 記錄器介面

若要開始使用記錄器，您必須建立`\Psr\Log\LoggerInterface`的執行個體。 使用此介面，您可以呼叫下列函式，將資料寫入記錄檔：

- [警報()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [緊急()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [錯誤()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [資訊()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [通知()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [警告()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

在[記錄檔資料庫活動](../logs/database-activity.md)範例中會說明執行此操作的一種方式。

另一種方式如下：

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

上述範例顯示`SomeModel`使用建構函式插入來接收`\Psr\Log\LoggerInterface`物件。 在方法`doSomething`中，如果發生某些錯誤，它會記錄到方法`critical` (`$this->logger->critical($e);`)。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424)定義了八個記錄層級（偵錯、資訊、通知、警告、錯誤、嚴重、警示和緊急）。
