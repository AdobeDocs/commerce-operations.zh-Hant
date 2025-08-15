---
title: ACSD-59865： [!UICONTROL Cart Price Rule]無法取消先前的規則，因為產品數量不足
description: 套用ACSD-59865修補程式以修正Adobe Commerce問題，其中*固定金額折扣、* *產品價格折扣百分比*和*購買X取得Y* [!UICONTROL Cart Price Rules]中的*折扣數量步驟*值不再取消先前規則的動作。
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865： [!UICONTROL Cart Price Rule]無法取消先前的規則，因為產品數量不足

ACSD-59865修補程式修正了&#x200B;*[!UICONTROL Discount quantity step]*、*[!UICONTROL Fixed amount discount]、*、*[!UICONTROL Percent of product price discount]和* *[!UICONTROL Buy X get Y]*&#x200B;中的[!UICONTROL Cart Price Rules]值不再取消先前規則的動作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-59865。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於購物車中的產品數量不足，[!UICONTROL Cart Price Rule]無法取消先前套用的規則。

<u>要再現的步驟</u>：

1. 以管理員身分登入。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;並按一下&#x200B;**[!UICONTROL Add New rule]**。
   * 設定&#x200B;**[!UICONTROL Rule Name]** = *測試 — 1*
   * 選取所有&#x200B;*網站*&#x200B;和&#x200B;*客戶群組*
   * 設定&#x200B;**[!UICONTROL Priority]** = *0*
   * 移至&#x200B;**[!UICONTROL Actions]**&#x200B;區段：
      * 設定&#x200B;**[!UICONTROL Apply]** = *產品價格折扣百分比*
      * 設定&#x200B;**[!UICONTROL Discount amount]** = *10*
      * 設定&#x200B;**[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * 設定&#x200B;**[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * 將&#x200B;**[!UICONTROL Discard subsequent rules]**&#x200B;設為&#x200B;*否*
1. 清除快取。
1. 前往店面，新增一個專案到購物車，然後繼續進行&#x200B;*結帳/購物車*。
1. 驗證購物車已套用&#x200B;*10%*&#x200B;折扣。
1. 返回&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;並建立新規則。
   * 設定&#x200B;**[!UICONTROL Rule Name]** = *測試 — 2*
   * 選取全部&#x200B;**[!UICONTROL Websites]**&#x200B;和&#x200B;**[!UICONTROL Customer Groups]**
   * 設定&#x200B;**[!UICONTROL Priority]** = *2*
   * 導覽至&#x200B;**[!UICONTROL Actions]**&#x200B;區段：
      * 設定&#x200B;**[!UICONTROL Apply]** = *產品價格折扣百分比*
      * 設定&#x200B;**[!UICONTROL Discount amount]** = *20*
      * 設定&#x200B;**[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * 設定&#x200B;**[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. 清除快取。
1. 再次返回店面。
1. 更新購物車以重新整理規則。 確認不再套用&#x200B;*10%*&#x200B;折扣。
1. 將專案新增到購物車，直到數量符合第二個規則所需的&#x200B;*步驟*&#x200B;值。

<u>預期結果</u>：

當符合第二個規則的條件時，會套用第一個[!UICONTROL Cart Price Rule]。

<u>實際結果</u>：

價格規則會套用至管理員儀表板中的設定。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
