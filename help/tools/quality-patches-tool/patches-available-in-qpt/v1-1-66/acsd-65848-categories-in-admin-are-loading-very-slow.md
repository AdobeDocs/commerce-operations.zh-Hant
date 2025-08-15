---
title: ACSD-65848：管理員中的類別載入速度非常慢
description: 套用ACSD-65848修補程式以修正Adobe Commerce使用子選取計算類別中產品總數的問題，這會延遲類別載入時間。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848：管理員中的類別載入速度非常慢

ACSD-65848修補程式修正使用子選取計算類別中產品總數的問題，這會延遲類別載入時間。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACSD-65848。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員類別檢視/編輯頁面在載入時會遭遇嚴重延遲。 延遲是由用來計算類別中產品總數的方法所造成，此方法有賴於子選取查詢。 重構此邏輯以改用連線可改善效能並減少載入時間。

<u>要再現的步驟</u>：

1. 使用2.4.8版建立新的Adobe Commerce Cloud例項。
1. 建立2,500個類別和至少10,000種產品：
   1. 將`setup/performance-toolkit`目錄複製到`./var`，以便您可以編輯設定檔。
   1. 開啟`small.xml`設定檔並更新為包含2,500個類別和250,000個產品（以符合商家設定）。
   1. 執行以下命令來產生夾具：

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. 建立產品和類別後，請確定所有類別皆設為錨點。 執行此SQL查詢：

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. 在「管理員」面板中，建立更深入的類別結構：
   * 將「類別1」下的「類別2」移至樹狀結構中較深的巢狀結構。
1. 嘗試使用下列URL在管理員面板中開啟類別頁面：
   ```/admin/catalog/category/edit/id/xx/```

<u>預期結果</u>：

每個類別頁面會在數秒內的第一次嘗試時開啟。

<u>實際結果</u>：

開啟類別頁面需要超過一分鐘的時間。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
