---
title: 記錄器介面
description: 開始使用記錄器介面。
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 記錄器介面

要開始使用記錄器，必須建立 `\Psr\Log\LoggerInterface`。 使用此介面，可以調用以下函式將資料寫入日誌檔案：

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [關鍵()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [緊急()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [錯誤()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [警告()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

要做到這一點，可在 [日誌資料庫活動](../logs/database-activity.md) 示例。

另一種方式是：

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

上例顯示 `SomeModel` 接收 `\Psr\Log\LoggerInterface` 對象。 在方法中 `doSomething`，如果發生錯誤，則記錄到方法 `critical` (`$this->logger->critical($e);`)。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) 定義8個日誌級別（debug、info、notice、warning、error、critical、alert和emergency）。