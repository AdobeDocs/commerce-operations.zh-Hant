---
title: ACP2E-4050： [!UICONTROL Free Shipping]未套用多重出貨簽出
description: 套用ACP2E-4050修補程式以修正Adobe Commerce的問題，即[!UICONTROL Free Shipping]包含子選取條件及特定價格的產品時，多重位址結帳期間未套用[!UICONTROL Cart Price Rules]。
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050： **[!UICONTROL Free Shipping]**&#x200B;未套用多重出貨簽出

ACP2E-4050修補程式修正了當&#x200B;**[!UICONTROL Free Shipping]**&#x200B;包含子選取條件及特定價格的產品時，多重運送結帳期間未套用&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACP2E-4050。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p10

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當&#x200B;**[!UICONTROL Free Shipping]**&#x200B;包含子選取條件和特定價格的產品時，多重送貨結帳期間不會套用&#x200B;**[!UICONTROL Cart Price Rules]**。

<u>要再現的步驟</u>：

1. 建立具有兩個地址的客戶帳戶。
1. 啟用&#x200B;**[!UICONTROL Free Shipping]**&#x200B;並將&#x200B;**[!UICONTROL Minimum Order Amount]**&#x200B;設定為&#x200B;*999999*。
1. 導覽至「[!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules]」，然後建立包含下列條件的購物車價格規則：

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. 安裝範例資料。
1. 將下列產品依指定順序新增至購物車：
   * Wayfarer Messenger包
   * Olivia 1/4 Zip Light Jacket
   * Sprite瑜伽伴侶套裝。
1. 開啟購物車並驗證&#x200B;**[!UICONTROL Free Shipping]**&#x200B;選項是否可用。
1. 按一下&#x200B;**[!UICONTROL Check Out with Multiple Addresses]**。
1. 選取簡易產品的其他送貨地址。
1. 按一下&#x200B;**[!UICONTROL Go to Shipping Information]**。

<u>預期結果</u>：

**[!UICONTROL Free Shipping]**&#x200B;適用於可設定和捆綁產品出貨。

<u>實際結果</u>：

**[!UICONTROL Free Shipping]**&#x200B;無法使用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
