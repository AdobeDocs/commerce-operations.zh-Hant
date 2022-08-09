---
title: 自定義日誌記錄
description: 瞭解如何使用自定義日誌記錄來調查錯誤。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# 自定義日誌記錄概述

日誌可提供系統進程的可視性；例如，調試有助於您瞭解錯誤發生時或導致錯誤的原因的資訊。

本主題重點介紹基於檔案的日誌記錄，儘管Commerce也提供了在資料庫中儲存日誌的靈活性。

Adobe建議使用集中式應用程式日誌記錄，原因如下：

- 它允許將日誌儲存在應用程式伺服器以外的伺服器上，並減少磁碟I/O操作，從而簡化了對應用程式伺服器的支援。

- 它使用特殊工具(如 [洛格斯塔什]。 [龍]或 [氟] — 不影響生產伺服器。

   >[!INFO]
   >
   >Adobe不建議或認可任何特定的日誌記錄解決方案。

## PSR-3合規性

的 [PSR-3標準][laminas] 為日誌庫定義通用的PHP介面。 PSR-3的主要目標是允許庫接收 `Psr\Log\LoggerInterface` 對象，並以簡單而通用的方式將日誌寫入其中。

這提供了易於替換實施的能力，而不用擔心這種替換可能會破壞應用程式碼。 它還保證即使在將來版本的系統中更改日誌實現，自定義元件也能正常工作。

## 獨白

Commerce 2符合PSR-3標準。 預設情況下，Commerce使用 [獨白]。 作為偏好實現的獨白 `Psr\Log\LoggerInterface` 中 [`di.xml`][di]。

Monolog是一種流行的PHP日誌記錄解決方案，它包含多種處理程式，使您能夠構建高級日誌記錄策略。 以下是Monolog的工作原理摘要。

獨白 _記錄器_ 是一條有自己的頻道 _處理程式_。 Monolog有許多處理劑，包括：

- 記錄到檔案和syslog
- 發送警報和電子郵件
- 記錄特定的伺服器和網路記錄
- 登錄正在開發（與FireBug和Chrome Logger等整合）
- 登錄到資料庫

每個處理程式都可以處理輸入消息並停止傳播，或者將控制傳遞給鏈中的下一個處理程式。

日誌消息可以採用多種不同方式處理。 例如，您可以將所有調試資訊儲存到磁碟上的檔案中，將日誌級別較高的消息放入資料庫，最後通過電子郵件發送日誌級別為「關鍵」的消息。

其它通道可以具有不同的一組處理程式和邏輯。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[氟]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[龍]: https://devcenter.heroku.com/articles/logplex
[洛格斯塔什]: https://www.elastic.co/products/logstash
[獨白]: https://github.com/Seldaek/monolog
