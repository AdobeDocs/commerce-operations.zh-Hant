---
title: ACP2E-3753：庫存警示電子郵件未在多重商店設定中使用商店特定的主題範本
description: 套用ACP2E-3753修補程式以修正Adobe Commerce問題，多商店設定中的產品警報電子郵件一律使用預設主題傳送，無論商店或主題設定為何。
feature: Themes, Personalization
role: Admin, Developer
source-git-commit: 6af6dc5d4880cc0cb80c443cab98cfb562949101
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACP2E-3753：庫存警示電子郵件未在多重商店設定中使用商店特定的主題範本

ACP2E-3753修補程式修正了多存放區設定中的產品警報電子郵件一律使用預設主題傳送的問題，而不論存放區或主題設定為何。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACP2E-3753。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p11

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

多商店設定中的產品警報電子郵件一律使用預設主題傳送，無論商店或主題設定為何。

<u>要再現的步驟</u>：

1. 建立兩個網站、商店和商店檢視。
1. 建立兩個獨立的主題，並將它們指派給不同的商店。
1. 產品警報設定是每分鐘執行的預設範圍。
1. 覆寫/新增兩個主題的部分內容至`stock.phtml`檔案。 檔案位置的範例：

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. 為每個商店建立使用者，並訂閱產品庫存警報。
1. 觸發產品庫存警報，以傳送電子郵件。

<u>預期結果</u>：

電子郵件應包含主題層級的變更。

<u>實際結果</u>：

電子郵件不包含個別網站/商店中設定的範本。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
