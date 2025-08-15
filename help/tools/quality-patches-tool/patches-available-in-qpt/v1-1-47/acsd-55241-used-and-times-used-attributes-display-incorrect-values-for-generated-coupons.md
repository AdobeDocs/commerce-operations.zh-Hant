---
title: ACSD-55241： **Used**和**Times Used**屬性針對產生的抵用券顯示不正確的值
description: Adobe Commerce套用ACSD-55241修補程式，修正**使用**和**使用次數**屬性針對產生的抵用券顯示不正確值的問題
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241： **已使用**&#x200B;和&#x200B;**已使用次數**&#x200B;屬性針對產生的抵用券顯示不正確的值

ACSD-55241修補程式修正了&#x200B;**已使用**&#x200B;及&#x200B;**已使用次數**&#x200B;屬性針對產生的抵用券顯示不正確值的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.47時，即可使用此修補程式。 修補程式ID為ACSD-55241。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**已使用**&#x200B;與&#x200B;**已使用次數**&#x200B;屬性針對產生的抵用券顯示不正確的值。

<u>要再現的步驟</u>：

1. 從&#x200B;**[!UICONTROL Cart Price Rules]** > **[!UICONTROL Admin]** > **[!UICONTROL Marketing]**&#x200B;建立&#x200B;**[!UICONTROL Promotion]**，並新增在下訂單時符合的任何條件（範例：小計大於&#x200B;*5$*）

   * 套用任何折扣。
   * 選取&#x200B;**[!UICONTROL Auto Coupon]**。
   * 它將從&#x200B;**管理優惠券代碼**&#x200B;產生一些優惠券代碼。
   * 重新索引並清除快取。

1. 建立&#x200B;**[!UICONTROL customer account]**&#x200B;並登入前端。
1. 新增購物車中超過&#x200B;*2*&#x200B;個數量的產品，並套用一張優惠券。
1. 按一下&#x200B;**[!UICONTROL Check Out with Multiple Addresses]**。
1. 為每個數量選取個別的地址、下訂單，然後完成結帳程式。
1. 觀察管理員的訂單總計，並檢視套用的折扣。
1. 使用其他優惠券再次下訂單。
1. 執行`php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &`命令以更新抵用券程式碼使用方式。

<u>預期結果</u>：

正確的計數應顯示在管理員中&#x200B;**的**&#x200B;已使用時間&#x200B;**和**&#x200B;已使用&#x200B;**欄，其中**&#x200B;有&#x200B;**[!UICONTROL manage coupon]**&#x200B;是&#x200B;**[!UICONTROL cart price rule]**&#x200B;值。

<u>實際結果</u>：

在優惠券格線的&#x200B;**已使用時間**&#x200B;資料行中，使用的優惠券代碼計數不會更新，而且如果您以多個送貨地址下訂單，**已使用**&#x200B;資料行會顯示&#x200B;*否*&#x200B;值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
