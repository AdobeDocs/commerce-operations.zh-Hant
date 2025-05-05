---
title: ACSD-62475：修正購物車中禮品卡合併的問題
description: 套用ACSD-62475修補程式，修正Adobe Commerce將不同詳細資料的禮品卡產品錯誤地合併至購物車中單一條列專案的問題。
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 7c35c245d6a464f7758053bd8aa1854c8fe8a5f2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475：修正購物車中禮品卡合併的問題

ACSD-62475修補程式修正禮卡產品不同詳細資料會不正確合併至購物車中單一條列專案的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62475。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

加入購物車且具有不重複寄件者或收件者詳細資料的禮品卡產品會不正確地合併至單一條列專案，導致資料不一致。

<u>要再現的步驟</u>：

1. 使用下列設定建立[!UICONTROL Gift Card]產品：
   * **[!UICONTROL Card Type]**： [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**： 10

1. 在店面，建立新使用者並登入。

1. 新增禮卡產品至購物車，並具備下列詳細資訊：
   * **[!UICONTROL Sender Name]**：寄件者1
   * **[!UICONTROL Sender Email**]： sender1@test.com
   * **[!UICONTROL Recipient Name**]：收件者1
   * **[!UICONTROL Recipient Email**]： recipient1@test.com


1. 登出

1. 將相同的禮品卡產品加入購物車，並附有下列詳細資料：
   * **[!UICONTROL Sender Name]**：寄件者2
   * **[!UICONTROL Sender Email**]： sender2@test.com
   * **[!UICONTROL Recipient Name**]：收件者2
   * **[!UICONTROL Recipient Email**]： recipient2@test.com

1. 重新登入並檢查購物車。

<u>預期結果</u>：

兩張禮品卡應該會顯示為兩個獨立的條列專案，並附上各自的詳細資料。

<u>實際結果</u>：

禮品卡會合併為一個數量為2的條列專案，保留第一張禮品卡的詳細資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
