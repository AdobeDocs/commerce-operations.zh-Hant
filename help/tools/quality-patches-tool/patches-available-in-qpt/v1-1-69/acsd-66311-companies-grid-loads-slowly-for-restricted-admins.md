---
title: ACSD-66311：受限制管理員使用者的公司格線載入緩慢
description: 套用ACSD-66311修補程式，修正Adobe Commerce網站存取受限的管理員使用者公司格線載入緩慢的問題。
role: Admin, Developer
feature: B2B
type: Troubleshooting
exl-id: e470078b-dd10-4b0b-a489-bc88f025fded
source-git-commit: 3337907b1893260d6cb18b1c4fbf45dfa1f3d6d5
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# ACSD-66311：受限制管理員使用者的公司格線載入緩慢

ACSD-66311修補程式修正具有受限制網站存取權的管理員使用者之公司格線載入緩慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66311。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

對於網站存取受限的管理員使用者，公司格線載入緩慢。

<u>要再現的步驟</u>：

1. 使用&#x200B;**[!UICONTROL B2B features]**&#x200B;安裝Adobe Commerce。
1. 使用商店/檢視建立2個額外的網站（除了主要網站之外）：
   * 主要網站（安裝期間建立）
   * 網站2 → Store 2 → StoreView 2
   * 網站3 → Store 3 → StoreView 3
1. 建立&#x200B;**[!UICONTROL Admins in Scope]**&#x200B;使用者角色：
   * 範圍：只有兩個存放區： *主要網站* + *網站3/存放區3*。
   * 資源：僅&#x200B;*儀表板* + *公司*。
1. 建立角色為&#x200B;**[!UICONTROL Admins in Scope]**&#x200B;的管理員使用者，例如&#x200B;**adminscope**。
1. 產生特定的分散式客戶和公司資料：
   1. **指派給網站的客戶**

      | 網站ID | 客戶數量 |
      |------------|---------------------|
      | 1 | 600,000 |
      | 2 | 1,500 |
      | 3 | 500 |

   1. 執行以下查詢以驗證分配：

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **指派給公司的客戶**

      | 客戶數量 | 公司數目 |
      |---------------------|---------------------|
      | 1 | 4,500 |
      | 2 | ~1,000 |
      | ~595k | 1 |

   1. 執行以下查詢以驗證分配：

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
              SELECT company_id, COUNT(customer_id) AS customer_count
              FROM company_advanced_customer_entity
              GROUP BY company_id
            ) AS subquery
            GROUP BY customer_count
            ORDER BY customer_count; 
      ```

1. 重新索引所有資料以產生&#x200B;**customer_grid_flat**&#x200B;中的專案。
1. 以&#x200B;**管理員範圍**&#x200B;登入。
1. 前往&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**。

<u>預期結果</u>：

頁面載入不到1秒。

<u>實際結果</u>：

載入頁面需要14分鐘以上的時間。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
