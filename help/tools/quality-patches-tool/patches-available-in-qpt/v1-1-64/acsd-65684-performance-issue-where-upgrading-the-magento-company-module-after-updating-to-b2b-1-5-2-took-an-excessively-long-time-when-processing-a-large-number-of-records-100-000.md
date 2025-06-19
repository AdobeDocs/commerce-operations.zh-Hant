---
title: ACSD-65684：在B2B 1.5.2中升級Magento_Company緩慢，company_structure中有超過100,000筆記錄
description: 套用ACSD-65684修補程式以修正Adobe Commerce的問題，其中升級B2B 1.5.2中的Magento_Company模組耗時過長，因為company_structure表格中處理大量記錄(~100,000+)。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684： [!DNL B2B] 1.5.2中的`Magento_Company`升級緩慢，`company_structure`中有超過100,000筆記錄

ACSD-65684修補程式修正了在[!DNL B2B] 1.5.2中升級`Magento_Company`模組時，處理`company_structure`表格中的100,000筆記錄所花時間過長的效能問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65684。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce B2B （所有部署方法） 1.5.2

**與Adobe Commerce版本相容：**

* Adobe Commerce B2B （所有部署方法） 1.5.2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

處理`company_structure`表格中100,000筆以上的記錄時，升級[!DNL B2B] 1.5.2中的`Magento_Company`模組所花費的時間過長，發生效能問題。

<u>要再現的步驟</u>：

1. 使用[!DNL B2B]安裝Adobe Commerce 2.4.7-p4。
1. 新增100,000筆記錄至`company_structure`資料表。
1. 升級至Adobe Commerce 2.4.7-p5和最新的[!DNL B2B]模組(1.5.2)。
1. 套用修補程式ACSD-65540。
1. 執行：

```
bin/magento setup:upgrade
```

<u>預期結果</u>：

`setup:upgrade`在合理的時間內完成。

<u>實際結果</u>：

`setup:upgrade`需要很長時間才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
