---
title: ACSD-50368：透過非同步REST API或非同步大量REST API建立客戶時，會忽略客戶group_id
description: 套用ACSD-50368修補程式以修正Adobe Commerce問題，該問題導致在透過非同步REST API或非同步大量REST API建立客戶時忽略客戶group_id。
feature: REST
role: Admin
exl-id: 1ca78717-2144-4410-a398-764864ee182f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-50368：透過非同步REST API或非同步大量REST API建立客戶時，會忽略客戶group_id

ACSD-50368修補程式修正了透過Async REST API或Async Bulk REST API建立客戶時，忽略客戶group_id的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-50368。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過非同步REST API或非同步大量REST API建立客戶時，會忽略客戶group_id。

<u>必要條件</u>：

設定RabbitMQ以處理佇列：

```
bin/magento setup:config:set --amqp-host=services --amqp-port=5672 --amqp-user=guest --amqp-password=guest 
bin/magento setup:upgrade --keep-generated
```

<u>要再現的步驟</u>

1. 使用非同步Rest API請求來建立客戶：

   ```
   curl --location 'https://site.test/rest/default/async/V1/customers' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Content-Type: application/json' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai' \
   --data-raw '{
       "customer": {
           "email": "foo@bar.test",
           "firstname": "Test",
           "lastname": "User",
           "group_id": 2
       }
   }
   ```

1. 會傳回類似的回應：

   ```
   {
       "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
       "request_items": [
           {
               "id": 0,
               "data_hash":   "6e718a93b02a30a98cb994d1c4e8cf1eeedcb962f384e4a463c"   ,
               "status": "accepted"
           }
       ],
       "errors": false
   }
   ```

1. 檢查此非同步請求的狀態：

   ```
   curl --location 'https://site.test/rest/default/V1/bulk/b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd/detailed-status' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai
   ```

<u>預期結果</u>：

新客戶的group_id正確設定為2。

<u>實際結果</u>：

針對新客戶，group_id會設定為預設值1。

```
{
    "operations_list": [
        {
            "id": 0,
            "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
            "topic_name": "async.magento.customer.api.accountmanagementinterface.createaccount.post",
            "serialized_data": null,
            "result_serialized_data": "{\"id\":4,\"group_id\":1,\"created_at\":\"2023-03-21 22:01:09\",\"updated_at\":\"2023-03-21 22:01:09\",\"created_in\":\"Default Store View\",\"email\":\"foo@bar.test\",\"firstname\":\"Test\",\"lastname\":\"User\",\"store_id\":1,\"website_id\":1,\"addresses\":[],\"disable_auto_group_change\":0,\"extension_attributes\":{\"is_subscribed\":false}}",
            "status": 1,
            "result_message": "Service execution success Magento\\Customer\\Model\\AccountManagement\\Interceptor::createAccount",
            "error_code": null
        }
    ],
        "user_type": 2,
        "bulk_id": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
        "description": "Topic async.magento.customer.api.accountmanagementinterface.createaccount.post",
        "start_time": "2023-03-21 22:01:09",
        "user_id": 1,
        "operation_count": 1
}
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
