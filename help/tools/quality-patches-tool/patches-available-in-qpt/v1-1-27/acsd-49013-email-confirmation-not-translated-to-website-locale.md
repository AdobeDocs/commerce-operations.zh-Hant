---
title: ACSD-49013：電子郵件確認未轉譯為網站地區設定
description: 套用ACSD-49013修補程式，修正Adobe Commerce使用大量API建立客戶時，電子郵件確認未轉譯為網站地區設定的問題。
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013：電子郵件確認未轉譯為網站地區設定

ACSD-49013修補程式修正了在使用大量API建立客戶時，電子郵件確認未轉譯為網站地區設定的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-49013。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用大量API建立客戶時，電子郵件確認未轉換為網站地區設定。

<u>要再現的步驟</u>：

1. 安裝其他地區設定，例如`de_DE`。
1. 設定&#x200B;*RabbitMQ*。
1. 執行`bin/magento setup:upgrade`以在RabbitMQ中安裝佇列並設定語言套件。
1. 在[!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;中建立其他網站。
1. 在[!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**&#x200B;中，將此新網站的地區設定設為`de_DE`。
1. 執行API呼叫，使用大量API建立客戶帳戶。 使用對應的`website_id`。

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. 執行`bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`。
1. 您可以看到客戶帳戶在指定的網站上正確建立。
1. 檢查收到的電子郵件以進行客戶註冊。

<u>預期結果</u>：

由於客戶是在指定的網站上建立，因此會使用該網站的地區設定來傳送註冊電子郵件。

<u>實際結果</u>：

客戶在指定的網站上正確建立，但在使用大量API時，會使用預設地區設定來傳送註冊電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
