---
title: ACSD-49480：捨棄無法使用的後續規則
description: 套用ACSD-49480修補程式以修正[!UICONTROL Cart Price Rule - Discard Subsequent Rules]無法如預期運作的Adobe Commerce問題。
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480： [!UICONTROL Cart Price Rule - Discard Subsequent Rules]未如預期運作

ACSD-49480修補程式修正[!UICONTROL Cart Price Rule - Discard Subsequent Rules]無法如預期運作的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-49480。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Cart Price Rule - Discard Subsequent Rules]未如預期運作。

<u>要再現的步驟</u>：

1. 使用優惠券代碼（將其命名為&#x200B;*TEST*）建立&#x200B;**[!UICONTROL Cart Price Rule]**，該代碼會為&#x200B;**[!UICONTROL Actions]**&#x200B;索引標籤中的&#x200B;*產品識別碼1*&#x200B;提供$10的折扣，其中[!UICONTROL Discard Subsequent Rules]設為&#x200B;*[!UICONTROL Yes]*，[!UICONTROL Priority]設為&#x200B;*1*。
1. 在&#x200B;**[!UICONTROL Actions]**&#x200B;索引標籤中建立另一個&#x200B;**[!UICONTROL Cart Price Rule]**，但不含贈券代碼，且在[!UICONTROL Priority]設為&#x200B;*2*&#x200B;的情況下，為&#x200B;*產品識別碼2*&#x200B;提供$5的折扣。 在此，我們假設這是針對&#x200B;*產品ID 2*&#x200B;的全球銷售。
1. 移至前端網站，並將&#x200B;*產品識別碼1*&#x200B;和&#x200B;*產品識別碼2*&#x200B;新增到購物車中。
1. 套用&#x200B;*TEST*&#x200B;優惠券代碼。

<u>預期結果</u>

* *折扣1*&#x200B;已套用至&#x200B;*產品識別碼1*。
* *折扣2*&#x200B;已套用至&#x200B;*產品識別碼2*。

<u>實際結果</u>

* 僅&#x200B;*折扣1*&#x200B;套用至&#x200B;*產品識別碼1*。
* *折扣2*&#x200B;未套用至&#x200B;*產品識別碼2*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
