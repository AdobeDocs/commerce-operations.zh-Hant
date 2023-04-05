---
title: 自訂cron工作和cron群組參考
description: 了解如何使用cron群組自訂cron。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 自訂規則參考

本主題可協助您設定自訂模組的crontab和選擇性cron群組。 如果您的自定義模組需要定期計畫任務，則必須為該模組設定crontab。 A _crontab_ 是cron作業設定。

（可選）您可以設定自訂群組，除其他事項外，這可讓您執行該群組中定義的cron作業，而不依賴其他cron作業。

如需逐步教學課程，請參閱 [設定自訂cron作業和cron群組（教學課程）](custom-cron-tutorial.md).

如需關於cron作業的概觀，請參閱 [設定cron作業](../cli/configure-cron-jobs.md).

## 設定cron群組

本節探討如何選擇為自訂模組建立cron群組。 如果您不需要，請繼續下一節。

A _cron組_ 是一個邏輯組，可讓您一次輕鬆為多個進程運行cron。 大部分的商務模組都使用 `default` 冠軍集團；部分模組使用 `index` 群組。

如果您要為自訂模組實作cron，可以選取使用 `default` 群組或其他群組。

**為模組設定cron群組**:

建立 `crontab.xml` 檔案（位於模組目錄中）:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

對於一個群組，檔案應包含下列內容：

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
| `group_name` | cron群組的名稱。 群組名稱不必是唯一的。 您一次可以對一個群組執行cron。 |
| `job_name` | 此cron作業的唯一ID。 |
| `classpath` | 要實例化的類（類路徑）。 |
| `method` | 中的方法 `classpath` 呼叫。 |
| `time` | 以cron格式排程。 如果在商務資料庫或其他儲存中定義了計畫，請忽略此參數。 |

產生的 `crontab.xml` 有兩個群組時，可能如下所示：

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

例如，請參閱 [Magento_客戶crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### 指定Cron組選項

您可以宣告新群組，並指定其設定選項（所有選項都在存放區檢視範圍中執行），透過 `cron_groups.xml` 檔案，位於：

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

以下是 `cron_groups.xml` 檔案：

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
| `schedule_generate_every` | 將排程寫入 `cron_schedule` 表格。 |
| `schedule_ahead_for` | 提前時間（以分鐘為單位）寫入 `cron_schedule` 表格。 |
| `schedule_lifetime` | 必須啟動cron作業或認為cron作業遺漏（「太遲」而無法執行）的時間窗口（以分鐘為單位）。 |
| `history_cleanup_every` | 該cron歷史記錄會保留在資料庫中的時間（以分鐘為單位）。 |
| `history_success_lifetime` | 已成功完成cron作業的記錄保留在資料庫中的時間（以分鐘為單位）。 |
| `history_failure_lifetime` | 在資料庫中保留失敗cron作業記錄的時間（以分鐘為單位）。 |
| `use_separate_process` | 在單獨的php進程中運行此cron組的作業 |

## 停用cron作業

Cron作業沒有 `disable` 功能 [觀察者](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 不過，您可以使用下列技術來停用cron作業： `schedule` 包含絕不會發生的日期的時間。

例如，停用 `visitor_clean` 定義的cron作業 `Magento_Customer` 模組：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

若要停用 `visitor_clean` cron工作、建立自訂模組並重新寫入 `visitor_clean` cron job `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

現在， `visitor_clean` cron作業已設定為2月30日00:00運行，該日期永遠不會發生。
