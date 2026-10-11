---
title: ACSD-50949：與SKU篩選器搭配使用時，進階搜尋中的價格篩選器不會傳回正確結果
description: 套用ACSD-50949修補程式來修正Adobe Commerce問題，該問題導致在搭配SKU篩選器使用時，進階搜尋中的價格篩選器無法傳回正確結果。
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 3%
---
# ACSD-50949：與SKU篩選器搭配使用時，進階搜尋中的價格篩選器沒有傳回正確結果

ACSD-50949修補程式修正了進階搜尋中的價格篩選器在搭配SKU篩選器使用時未傳回正確結果的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-50949。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 問題

與SKU篩選器搭配使用時，進階搜尋中的價格篩選器沒有傳回正確結果。

<u>要再現的步驟</u>：

1. 建立多個產品，例如：

   | SKU | 名稱 | 價格 | 數量 |
   |-----|-----------|-------|----------|
   | MJ1 | 產品1 | $10 | 10 |
   | MJ2 | 產品2 | $15 | 10 |
   | MJ3 | 產品3 | $21 | 10 |
   | MJ4 | 產品4 | $32 | 10 |
   | MJ5 | 產品5 | $33 | 10 |
   | MJ6 | 產品6 | $34 | 10 |
   | MJ7 | 產品7 | $44 | 10 |

1. 在店面開啟&#x200B;**[!UICONTROL Advanced Search]**&#x200B;並依SKU搜尋： &quot;MJ&quot;。
1. 按一下&#x200B;**[!UICONTROL Modify your search]**&#x200B;連結。
1. 將價格範圍新增至從&#x200B;*1*&#x200B;到&#x200B;*21*&#x200B;的條件，然後按一下&#x200B;**[!UICONTROL Search]**&#x200B;按鈕。

<u>預期結果</u>：

系統只會傳回價格在定義範圍內的產品。

<u>實際結果</u>：

會傳回價格高於&#x200B;*$21*&#x200B;的產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
