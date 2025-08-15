---
title: 自訂cron工作和cron群組參考
description: 瞭解如何使用cron群組自訂cron。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 自訂crons參考

此主題可協助您為自訂模組設定crontab以及選擇性的cron群組。 如果您的自訂模組需要定期排程工作，您必須為該模組設定crontab。 _crontab_&#x200B;是cron工作設定。

您可以視需要設定自訂群組，以執行該群組中所定義的cron工作，而不受其他cron工作影響。

如需逐步教學課程，請參閱[設定自訂cron作業和cron群組（教學課程）](custom-cron-tutorial.md)。

如需cron作業的概觀，請參閱[設定cron作業](../cli/configure-cron-jobs.md)。

## 設定cron群組

本節探討如何選擇為自訂模組建立cron群組。 如果您不需要執行此動作，請繼續下一區段。

_cron群組_&#x200B;是邏輯群組，可讓您一次輕鬆執行一個以上處理程式的cron。 大部分的Commerce模組都使用`default` cron群組；有些模組則使用`index`群組。

如果您正在實作自訂模組的cron，您可以選擇使用`default`群組或其他群組。

**若要設定模組**&#x200B;的cron群組：

在您的模組目錄中建立`crontab.xml`檔案：

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

對於一個群組，檔案應具有以下內容：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

其中：

| 值 | 說明 |
|---|---|
| `group_name` | cron群組的名稱。 群組名稱不必是唯一的。 您可以一次對一個群組執行cron。 |
| `job_name` | 此cron作業的唯一ID。 |
| `classpath` | 要具現化的類別（類別路徑）。 |
| `method` | `classpath`中要呼叫的方法。 |
| `time` | 以cron格式排程。 如果排程定義於Commerce資料庫或其他儲存體中，請忽略此引數。 |

產生的具有兩個群組的`crontab.xml`可能如下所示：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

例如，請參閱[Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml)。

### 指定Cron群組選項

您可以透過位於下列位置的`cron_groups.xml`檔案宣告新群組並指定其組態選項（所有選項都在存放區檢視範圍中執行）：

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

以下是`cron_groups.xml`檔案的範例：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

其中：

| 選項 | 說明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 排程寫入`cron_schedule`表格的頻率（以分鐘為單位）。 |
| `schedule_ahead_for` | 排程寫入`cron_schedule`資料表的提前時間（分鐘）。 |
| `schedule_lifetime` | cron工作必須開始或認為cron工作已錯過（「太晚而無法執行」）的時間視窗（以分鐘為單位）。 |
| `history_cleanup_every` | cron記錄保留在資料庫中的時間（分鐘）。 |
| `history_success_lifetime` | 成功完成的cron工作記錄保留在資料庫中的時間（分鐘）。 |
| `history_failure_lifetime` | 失敗的cron作業記錄保留在資料庫中的時間（分鐘）。 |
| `use_separate_process` | 在單獨的php程式中執行此cron群組的作業 |

## 停用cron工作

Cron工作沒有我們為`disable`觀察者[所擁有的](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers)功能。 但是，可以使用下列技巧停用cron工作： `schedule`一次包含永遠不會發生的日期的時間。

例如，停用`visitor_clean`模組中定義的`Magento_Customer` cron工作：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

若要停用`visitor_clean` cron工作，請建立自訂模組並重寫`visitor_clean` cron工作`schedule`：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

現在，`visitor_clean` cron工作已設定在2月30日的00:00執行 — 絕不會發生的日期。
