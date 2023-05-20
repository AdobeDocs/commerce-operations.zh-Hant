---
title: 自定義cron作業和cron組引用
description: 瞭解如何使用cron組自定義cron。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 自定義crons引用

本主題可幫助您設定crontab和cron組（可選）以用於自定義模組。 如果您的自定義模組需要定期安排任務，則必須為該模組設定crontab。 A _crontab_ 是cron作業配置。

（可選）您可以設定自定義組，該組除其它外，還允許您運行在該組中定義的cron作業，而與其它cron作業無關。

有關逐步教程，請參見 [配置自定義cron作業和cron組（教程）](custom-cron-tutorial.md)。

有關cron作業的概覽，請參閱 [配置cron作業](../cli/configure-cron-jobs.md)。

## 配置cron組

本節討論如何選擇為自定義模組建立cron組。 如果不需要執行此操作，請繼續下一節。

A _cron組_ 是一個邏輯組，使您一次可以輕鬆運行多個進程的cron。 大多數Commerce模組使用 `default` 克隆集團；某些模組使用 `index` 組。

如果要為自定義模組實現cron，則可以選擇使用 `default` 或其他組。

**為模組配置克隆組**:

建立 `crontab.xml` 檔案位於模組目錄中：

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

對於一個組，檔案應包含以下內容：

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

位置：

| 值 | 說明 |
|---|---|
| `group_name` | cron組的名稱。 組名稱不必唯一。 一次可以為一個組運行cron。 |
| `job_name` | 此cron作業的唯一ID。 |
| `classpath` | 要實例化的類（類路徑）。 |
| `method` | 中的方法 `classpath` 打給你。 |
| `time` | 以cron格式計畫。 如果計畫是在Commerce資料庫或其他儲存中定義，請忽略此參數。 |

結果 `crontab.xml` 兩個組可能如下所示：

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

例如，請參見 [Magento_客戶crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml)。

### 指定Cron組選項

您可以通過 `cron_groups.xml` 檔案，位於：

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

下面是 `cron_groups.xml` 檔案：

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

位置：

| 選項 | 說明 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 將調度寫入到 `cron_schedule` 的子菜單。 |
| `schedule_ahead_for` | 時間（以分鐘為單位）提前將計畫寫入 `cron_schedule` 的子菜單。 |
| `schedule_lifetime` | cron作業必須啟動或cron作業被視為已錯過（「太遲」無法運行）的時間窗口（以分鐘為單位）。 |
| `history_cleanup_every` | cron歷史記錄保存在資料庫中的時間（以分鐘為單位）。 |
| `history_success_lifetime` | 成功完成的cron作業記錄保存在資料庫中的時間（分鐘）。 |
| `history_failure_lifetime` | 在資料庫中保存失敗cron作業記錄的時間（以分鐘為單位）。 |
| `use_separate_process` | 在單獨的php進程中運行此cron組的作業 |

## 禁用cron作業

Cron作業沒有 `disable` 像我們 [觀察](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers)。 但是，可以使用以下技術禁用cron作業： `schedule` 包含永遠不會發生的日期的時間。

例如，禁用 `visitor_clean` cron作業在 `Magento_Customer` 模組：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

禁用 `visitor_clean` cron作業，建立自定義模組並重寫 `visitor_clean` 克倫 `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

現在， `visitor_clean` cron作業已設定為在2月30日00點運行，該日期永遠不會發生。
