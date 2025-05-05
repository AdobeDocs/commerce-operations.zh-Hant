---
title: 會話儲存位置
description: 瞭解會話檔的存儲位置。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 會話儲存位置

本主題討論如何查找會話檔的存儲位置。 系統使用以下邏輯來商店會話檔：

- 如果配置了記憶體緩存，則會話存儲在 RAM 中;請參閱 [將 memcached 用於會話儲存](memcached.md)。
- 如果您配置了 Redis，會話將存儲在 Redis 伺服器上;請參閱將 [Redis 用於會話儲存](../cache/redis-session.md)。
- 如果您使用的是預設的基於文件的會話儲存，我們將按顯示的順序在以下位置商店會話：

   1. 中定義的目錄 [`env.php`](#example-in-envphp)
   1. 中定義的目錄 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 目錄

## 範例 `env.php`

下面是一個範例 `<magento_root>/app/etc/env.php` 片段：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

前面的示例將會話檔存儲在 `/var/www/session`

## `php.ini`中的範例

作為具有 `root` 許可權的用戶，請打開文件 `php.ini` 並搜尋以獲取 的值 `session.save_path`。 這標識了會話的存儲位置。

## 管理會話大小

[請參閱使用者指南&#x200B;_中的_&#x200B;會話管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management)。

## 垃圾集合配置

為了清理過期的會話，系統會根據指令計算`gc_probability / gc_divisor`的概率隨機調用`gc`（_垃圾集合_）處理程式。例如，如果將這些指令`1/100`分別設置為，則表示概率（`1%`_每 100 個請求_&#x200B;調用一次垃圾集合的概率）。

垃圾集合處理程式使用 `gc_maxlifetime` 指令，即會話被視為 _垃圾_ 並可能被清理的秒數。

在某些操作系統（Debian/Ubuntu）上，預設 `session.gc_probability` 指令是 `0`，這會阻止垃圾集合處理程序運行。

您可以覆寫`session.gc_`檔案中檔案中的`php.ini` `<magento_root>/app/etc/env.php`指令：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

配置會有所不同，具體取決於商家網站流量和特定需求。
