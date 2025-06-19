---
title: ACSD-48204：根據*是/否*屬性建立的型錄價格規則不會考慮選取的範圍
description: 套用ACSD-48204修正程式，修正根據*是/否*屬性建立的型錄價格規則未考慮所選範圍的Adobe Commerce問題。
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204：根據&#x200B;*是/否*&#x200B;屬性建立的型錄價格規則不考慮選取的範圍

ACSD-48204修補程式修正了根據&#x200B;*是/否*&#x200B;屬性建立的目錄價格規則未考慮所選範圍的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-48204。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

根據&#x200B;*是/否*&#x200B;屬性建立的型錄價格規則未考慮選取的範圍。

<u>要再現的步驟</u>：

1. 建立兩個網站（預設和W2）。
1. 建立&#x200B;*是/否*&#x200B;型別的產品屬性。
   * 設定[!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 根據具有兩個變數（V1和V2）的任何屬性建立可設定的產品。
   * 將&#x200B;*是/否*&#x200B;屬性新增至可設定的變數屬性集
   * 針對其中一個變數(V1)，在非預設網站(W2)上將值設定為&#x200B;*[!UICONTROL Yes]*
1. 建立目錄規則：
   * 已套用至兩個網站
   * 條件： *是/否*&#x200B;屬性值是&#x200B;*[!UICONTROL Yes]*
   * 折扣= 50%
1. 在非預設網站(W2)上開啟可設定的產品。
1. 檢查V1變化是否已套用50%的折扣。
1. 在Adobe Commerce管理員中開啟V1變數。
   * 切換至預設網站
   * 不做變更並儲存產品
1. 重新整理可設定的產品店面頁面。

<u>預期結果</u>：

由於未進行任何變更，V1變化仍套用50%折扣。

<u>實際結果</u>：

折扣會消失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
