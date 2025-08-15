---
title: ACP2E-3789：透過WebAPI在產品更新上複製的媒體檔案
description: 套用ACP2E-3789修補程式來修正Adobe Commerce的問題，若在提供媒體ID時透過WebAPI進行產品更新會複製媒體檔案。
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 1eaa8ed0-fde6-47c4-9339-8f5e7bce7b19
source-git-commit: f82dcd6c76ba3512e59275c26815b6bb89e53733
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACP2E-3789：透過WebAPI在產品更新上複製的媒體檔案

ACP2E-3789修補程式修正了提供媒體ID時，透過WebAPI進行產品更新時複製媒體檔案的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACP2E-3789。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過WebAPI更新具有媒體ID的產品會導致系統複製而不是取代媒體檔案、使用每個API呼叫建立新檔案，並導致影像的建置，而承載`/pub/media/catalog/products/cache/`目錄。

<u>要再現的步驟</u>：

1. 建立產品並新增影像。
1. 在`base_url/rest/V1/products/<sku>`使用REST API取得產品詳細資料。
1. 執行PUT要求以更新產品，保留`media_gallery_entrie`不變（相同的影像名稱和檔案）。
1. 檢查更新前後的`pub/media/catalog/product/xx/yy`目錄。

<u>預期結果</u>：

當請求中包含媒體ID時，影像檔案會被取代。

<u>實際結果</u>：

影像會以新名稱複製（例如wb04-blue-1.jpg），造成不必要的檔案棧疊。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
