---
title: ACSD-63139：當產品屬性包含數千個選項值時，產品匯出會失敗
description: 套用ACSD-63139修補程式，修正當產品屬性包含數千個選項值時，產品匯出失敗的Adobe Commerce問題。
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139：當產品屬性包含數千個選項值時，產品匯出會失敗

ACSD-63139修補程式修正產品屬性包含數千個選項值時產品匯出失敗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-63139。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當產品屬性包含數千個選項值時，產品匯出會失敗。

<u>要再現的步驟</u>：

1. 使用B2B模組安裝Adobe Commerce。
1. 匯入大型資料庫傾印：
    — 約7,000種產品
   &#x200B;- ~450個產品屬性
    — 某些屬性的選項超過100個
1. 執行以下命令以安裝cron （如果尚未安裝）：

   ```
   bin/magento cron:install
   ```

1. 依照[!DNL RabbitMQ]必要條件[[!DNL RabbitMQ] 中的指示設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/rabbitmq)。
1. 開啟`php.ini`檔案，將記憶體限制設定為4G，然後重新啟動PHP服務。
1. 在管理面板中，移至&#x200B;**[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**。
1. 在&#x200B;*[!UICONTROL Export Settings]*&#x200B;區段中，將&#x200B;**[!UICONTROL Entity Type]**&#x200B;設為&#x200B;*產品*，捲動至底部並按一下&#x200B;**[!UICONTROL Continue]**。
1. 執行以下命令以啟動匯出處理器：

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>預期結果</u>：

產品匯出應會成功完成。

<u>實際結果</u>：

產品匯出程式失敗，並傳回下列嚴重錯誤：

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
