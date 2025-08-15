---
title: ACSD-65822：搭售方案與可設定的產品數量未正確反映在購物車中
description: 套用ACSD-65822修補程式，以修正新增套件組合產品時，在管理面板的客戶購物車區段中，數量顯示為0的Adobe Commerce問題。
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822： [!UICONTROL Shopping Cart]中未正確反映套件組合和可設定的產品數量

ACSD-65822修補程式修正&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;下的&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;區段中無法正確顯示套件組合和可設定產品數量的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-65822。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;下的&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;區段中，未正確顯示組合和可設定的產品數量。

<u>要再現的步驟</u>：

1. 在店面建立使用者。
2. 在管理面板中建立&#x200B;**[!UICONTROL Bundle product]**。
3. 在店面，以登入使用者的身分，將搭售方案產品加入具有指定數量的購物車。
4. 在&#x200B;*管理員*&#x200B;面板中，移至&#x200B;**[!UICONTROL Customers]**&#x200B;並按一下步驟1中所建立之客戶的&#x200B;**[!UICONTROL Edit]**。
5. 按一下&#x200B;**[!UICONTROL Create Order]**。
6. 在左側的&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;下方，檢查&#x200B;**[!UICONTROL Shopping Cart]**&#x200B;區段。 您應該會看見束產品以及選取的數量。

<u>預期結果</u>：

束專案數量應該與店面上顯示的數量相符。

<u>實際結果</u>：

束專案數量顯示為0。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
