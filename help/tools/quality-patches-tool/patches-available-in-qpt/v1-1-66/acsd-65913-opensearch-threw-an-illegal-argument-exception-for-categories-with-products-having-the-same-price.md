---
title: ACSD-65913： [!DNL OpenSearch] 針對具有相同價格的類別擲回illegal_argument_exception
description: 套用ACSD-65913修補程式以修正Adobe Commerce的問題，即 [!DNL Opensearch] 在包含相同價格之所有產品的類別上擲回illegal_argument_exception （「[from]引數不能為負數」）。
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913： [!DNL OpenSearch]會針對具有相同價格之產品的類別擲回`illegal_argument_exception`

ACSD-65913修補程式修正產品價格相同的類別中，[!DNL OpenSearch]擲回`illegal_argument_exception`的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-65913。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

載入所有產品共用相同價格的類別時，[!DNL OpenSearch]擲回`illegal_argument_exception` （*[from]引數不能為負數*）。

<u>要再現的步驟</u>：

1. 安裝[!DNL OpenSearch] 2.19.1版，並將其設定為預設搜尋引擎。
1. 將&#x200B;**[!UICONTROL Price]**&#x200B;產品屬性設定為在階層導覽中可見：
   1. **[!UICONTROL Visible in Advanced Search]**： *是*
   1. **[!UICONTROL Comparable on Storefront]**： *是*
   1. **[!UICONTROL Use in Layered Navigation]**： *可篩選（含結果）*
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**」。 將&#x200B;**[!UICONTROL Price Navigation Step Calculation]**&#x200B;設定為&#x200B;*自動（平均產品計數）*。
1. 建立一個類別，其中包含6項價格相同的產品：
   1. SKU：product_super_0-1-1-1，價格：150美元
   1. SKU：product_super_0-1-1，價格：48美元
   1. SKU：product_super_0-1，價格：48美元
   1. SKU：product_super_0，價格：48美元
   1. SKU：product_super_0-1-1-1-1-1-1-1-1-1-1-1-1，價格：48美元
   1. SKU：product_super_0-1-1-1-1-1-1-1-1-1，價格：48美元
1. 執行以下命令：
   `bin/magento indexer:reindex`
1. 開啟類別頁面。 您會看到錯誤：
   *[from]引數不能為負數，找到[-1]*

<u>預期結果</u>：

當類別中的所有產品價格相同時，[!DNL OpenSearch]不應擲回`illegal_argument_exception`。

<u>實際結果</u>：

* [!DNL OpenSearch]擲回`illegal_argument_exception`訊息：
  *[from]引數不能為負數，找到[-1]*

* `var/log/exception.log`檔案包含：

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
