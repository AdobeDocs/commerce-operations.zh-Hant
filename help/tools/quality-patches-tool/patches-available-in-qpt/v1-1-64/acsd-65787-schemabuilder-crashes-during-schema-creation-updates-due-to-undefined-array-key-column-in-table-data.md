---
title: ACSD-65787：由於表格資料中未定義的陣列索引鍵「欄」，SchemaBuilder在結構描述建立或更新期間當機
description: 套用ACSD-65787修補程式，修正Adobe Commerce中在結構描述建立或更新期間，由於處理表格資料時未定義的陣列索引鍵「欄」而SchemaBuilder類別當機的問題。
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787：由於資料表資料中未定義的陣列索引鍵「資料行」，`SchemaBuilder`會在結構描述建立或更新期間當機

ACSD-65787修補程式修正了架構建立期間`SchemaBuilder`類別當機，或處理表格資料時由於未定義的陣列索引鍵「欄」而更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65787。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`SchemaBuilder`類別會在結構描述建立期間當機，或在處理資料表資料時由於未定義的陣列索引鍵「資料行」而更新。

<u>要再現的步驟</u>：

1. 執行以下命令：

```
bin/magento setup:upgrade
```

<u>預期結果</u>：

沒有錯誤。

<u>實際結果</u>：

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
