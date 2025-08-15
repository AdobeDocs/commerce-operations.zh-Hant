---
title: AC-14984： php-amqplib/php-amqplib ^3.2.0的SSL連線問題
description: 套用AC-14984修補程式，修正使用php-amqplib/php-amqplib ^3.2.0版時，SSL連線失敗並出現錯誤的Adobe Commerce問題。
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: cf46cd16-ef09-406a-835a-e5973887248f
source-git-commit: a934b02d42a5b9d2de722ebb6ef379ccca54649c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# AC-14984： php-amqplib/php-amqplib ^3.2.0的SSL連線問題

AC-14984修補程式修正使用`php-amqplib/php-amqplib`版本`^3.2.0`時，SSL連線失敗並出現錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為AC-14984。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p10

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p10 - 2.4.6-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用`php-amqplib/php-amqplib`版本`^3.2.0`時，SSL連線失敗並出現錯誤。

<u>要再現的步驟</u>：

1. 在`app/env.php`中設定SSL連線：

```
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
        'verify_peer' => true,
        'verify_peer_name' => false
      ],
    ),
  ),
```

1. 如果這是您第一次設定佇列，請執行`bin/magento setup:upgrade`。
1. 執行任何佇列取用者，例如： `bin/magento queue:consumers:start async.operations.all`

<u>預期結果</u>：

佇列取用者會啟動並處理訊息，而不會發生錯誤。

<u>實際結果</u>：

紀錄中會出現錯誤訊息：

```
{
  "message": "Invalid frame type 21",
  "context": {},
  "level": "error",
  "level_name": "ERROR",
  "channel": "report",
  "datetime": "2025-05-14T07:00:00.000000+00:00",
  "extra": {},
  "@timestamp": "2025-05-14T07:00:00.000000X",
  "severity": "ERROR",
  "original_level": 400,
  "full_message": "Invalid frame type 21\n#0 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(651): PhpAmqpLib\\Connection\\AbstractConnection->wait_frame(3.0)\n#1 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(235): PhpAmqpLib\\Connection\\AbstractConnection->wait_channel(0, 3.0)\n#2 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(352): PhpAmqpLib\\Channel\\AbstractChannel->next_frame(3.0)\n#3 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(264): PhpAmqpLib\\Channel\\AbstractChannel->..."
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
