---
title: ACSD-65540：發生SQL錯誤的原因是company_structure更新中缺少REGEXP_LIKE函式
description: 套用ACSD-65540修補程式來修正Adobe Commerce問題，該問題導致在company_structure更新中缺少REGEXP_LIKE函式而發生SQL錯誤。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# ACSD-65540： `REGEXP_LIKE`更新中遺失`company_structure`函式，導致SQL錯誤發生

ACSD-65540修補程式修正了`REGEXP_LIKE`更新中遺失`company_structure`函式而發生SQL錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65540。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce B2B （所有部署方法） 1.5.2

**與Adobe Commerce版本相容：**

* Adobe Commerce B2B （所有部署方法） 1.5.2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於`REGEXP_LIKE`更新中遺失`company_structure`函式，而發生SQL語法錯誤。

<u>要再現的步驟</u>：

1. 將[!DNL B2B]更新至1.5.2版。
1. 執行以下命令：

```
bin/magento setup:upgrade
```

<u>預期結果</u>：

升級成功完成。

<u>實際結果</u>：

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
