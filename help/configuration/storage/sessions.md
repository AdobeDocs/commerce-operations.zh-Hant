---
title: 會話儲存位置
description: 瞭解會話檔案的儲存位置。
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# 會話儲存位置

本主題討論如何查找會話檔案的儲存位置。 系統使用以下邏輯儲存會話檔案：

- 如果配置了memcached ，則會話會儲存在RAM中；見 [將memcached用於會話儲存](memcached.md)。
- 如果配置了Redis，則會話會儲存在Redis伺服器上；見 [將Redis用於會話儲存](../cache/redis-session.md)。
- 如果您使用預設的基於檔案的會話儲存，我們將會話按顯示的順序儲存在以下位置：

   1. 在中定義的目錄 [`env.php`](#example-in-envphp)
   1. 在中定義的目錄 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 目錄

## 示例 `env.php`

示例代碼段 `<magento_root>/app/etc/env.php` 如下：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上面的示例將會話檔案儲存在 `/var/www/session`

## 示例 `php.ini`

作為用戶 `root` 權限，開啟 `php.ini` 檔案並搜索 `session.save_path`。 這標識會話的儲存位置。

## 管理會話大小

查看 [會話管理](https://docs.magento.com/user-guide/stores/security-session-management.html) 的 _使用手冊_。

## 垃圾回收配置

要清除過期的會話，系統將調用 `gc` (_垃圾回收_)處理程式根據由 `gc_probability / gc_divisor` 指令。 例如，如果將這些指令設定為 `1/100` 分別表示 `1%` (_每100個請求一次調用垃圾回收的概率_)。

垃圾收集處理程式使用 `gc_maxlifetime` 指令 — 會話被視為的秒數 _垃圾_ 可能會被清除。

在某些作業系統(Debian/Ubuntu)上，預設 `session.gc_probability` 指令 `0`，這將阻止垃圾收集處理程式運行。

可以覆蓋 `session.gc_` 指令 `php.ini` 檔案 `<magento_root>/app/etc/env.php` 檔案：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

配置因通信量和商家網站的特定需求而異。
