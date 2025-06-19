---
title: ACSD-47232：核取[!UICONTROL Same as Billing Address]時未套用抵用券
description: 套用ACSD-47232修補程式以修正核取[!UICONTROL Same as Billing Address]時未套用優惠券的Adobe Commerce問題。
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232：核取[!UICONTROL Same as Billing Address]時未套用抵用券

ACSD-47232修補程式修正核取&#x200B;**[!UICONTROL Same as Billing Address]**&#x200B;時未套用抵用券的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23時，即可使用此修補程式。 修補程式ID為ACSD-47232。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

核取&#x200B;**[!UICONTROL Same as Billing Address]**&#x200B;時未套用抵用券。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 建立重量= *8*&#x200B;的簡單產品。
1. 建立具有預設帳單和送貨地址的新客戶。
1. 使用優惠券建立購物車價格規則。
   * 在&#x200B;**[!UICONTROL Conditions]**&#x200B;區段中，加入&#x200B;*總權重等於或大於5*
1. 嘗試在[!UICONTROL Commerce] Admin中建立新訂單。
   * 使用剛才建立的客戶
   * 新增產品
   * 嘗試套用抵用券

<u>預期結果</u>：

已套用抵用券。

<u>實際結果</u>：

您收到類似下列的錯誤： *123優惠券代碼無效。 請驗證程式碼，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
