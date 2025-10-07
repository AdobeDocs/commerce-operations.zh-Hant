---
title: 工作階段儲存位置
description: 瞭解Adobe Commerce中的工作階段儲存位置與檔案管理。 探索儲存邏輯和設定選項。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# 工作階段儲存位置

本主題說明如何找出工作階段檔案的儲存位置。 系統會使用以下邏輯來儲存工作階段檔案：

- 如果您已設定memcached，工作階段會儲存在RAM中；請參閱[使用工作階段儲存的memcached](memcached.md)。
- 如果您已設定Redis，工作階段會儲存在Redis伺服器上；請參閱[使用Redis作為工作階段儲存體](../cache/redis-session.md)。
- 如果您使用預設的檔案式工作階段儲存，我們會依照顯示的順序將工作階段儲存在下列位置：

   1. 在[`env.php`](#example-in-envphp)中定義的目錄
   1. 在[`php.ini`](#example-in-phpini)中定義的目錄
   1. `<magento_root>/var/session`目錄

## `env.php`中的範例

`<magento_root>/app/etc/env.php`中的範常式式碼片段如下：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上述範例將工作階段檔案儲存在`/var/www/session`

## `php.ini`中的範例

以具有`root`許可權的使用者身分，開啟您的`php.ini`檔案並搜尋`session.save_path`的值。 這會識別工作階段的儲存位置。

## 管理工作階段大小

請參閱[使用手冊](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management)中的&#x200B;_工作階段管理_。

## 記憶體回收組態

若要清除過期的工作階段，系統會根據`gc`指示詞計算的機率，隨機呼叫&#x200B;_（_&#x200B;記憶體回收`gc_probability / gc_divisor`）處理常式。 例如，如果您分別將這些指示詞設為`1/100`，則表示`1%`的機率（每100個要求中&#x200B;_次呼叫記憶體回收的機率_）。

記憶體回收處理常式使用`gc_maxlifetime`指示詞 — 工作階段被視為&#x200B;_記憶體_&#x200B;且可能被清理的秒數。

在某些作業系統(Debian/Ubuntu)上，預設`session.gc_probability`指示詞是`0`，可防止記憶體回收處理常式執行。

您可以覆寫`session.gc_`檔案中`php.ini`檔案的`<magento_root>/app/etc/env.php`指示：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

此設定會依流量和商家網站的特定需求而有所不同。
