---
title: ACSD-61845：請求包含text/html accept標頭時發生錯誤
description: 套用ACSD-61845修補程式來修正Adobe Commerce的問題，即傳送僅含*text/html* accept標頭的HTTP請求會造成500錯誤，並安裝B2B模組。
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
source-git-commit: 29845fd4a8c1c744aa780e60bb4154dfc3c1a02c
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845：含&#x200B;*text/html*&#x200B;接受標頭的請求發生錯誤

ACSD-61845修補程式修正了僅含&#x200B;*text/html*&#x200B;接受標頭的HTTP請求中，由於回應處理中的媒體型別不相符，而導致500錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61845。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

傳送accept標頭中只有&#x200B;*text/html*&#x200B;的HTTP要求時，因為媒體型別設定不符，而發生500錯誤。

<u>必要條件</u>：

B2B模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 傳送在accept標頭中只有&#x200B;*text/html*&#x200B;的請求，如下所示：

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>預期結果</u>：

傳回的頁面含有&#x200B;*200狀態碼*。

<u>實際結果</u>：

傳回500錯誤，在`exception.log`中出現下列錯誤訊息：

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
