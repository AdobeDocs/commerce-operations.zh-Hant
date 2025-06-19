---
title: ACSD-65223：針對B2B採購單手動選取的條款與協定會產生錯誤
description: 套用ACSD-65223修補程式以修正Adobe Commerce問題，該問題導致使用[!UICONTROL Purchase Orders]建立的訂單無法透過線上付款方式（如信用卡）在需要結帳的條款與條件時完成。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-65223：針對B2B採購單手動選取的條款與協定會產生錯誤

ACSD-65223修補程式修正了以下問題：當需要結帳的條款與條件時，使用&#x200B;**[!UICONTROL Purchase Orders]**&#x200B;建立的訂單無法透過信用卡等線上付款方式完成。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64時，即可使用此修補程式。 修補程式ID為ACSD-65223。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） B2B 1.5.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） B2B 1.5.1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果下訂單需要條款與條件，而您正嘗試完成使用[!UICONTROL Purchase Orders]建立的訂單，則無法使用信用卡等線上付款方式下訂單。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**」並選擇「**[!UICONTROL B2B Features]**」。
1. 將&#x200B;**[!UICONTROL Enable Company]**&#x200B;和&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;設定為&#x200B;*是*。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]**」並建立新條件。 將&#x200B;**[!UICONTROL Applied]**&#x200B;設為&#x200B;*[!UICONTROL Manually]*。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]**&#x200B;並將&#x200B;**[!UICONTROL Enable Terms and Conditions]**&#x200B;設定為&#x200B;*是*。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]**」並設定[!DNL Braintree]。
1. 在店面，建立一個公司。
1. 在管理員中，移至&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**。
1. 核准公司並允許&#x200B;**[!UICONTROL Purchase Orders]**。
1. 在前端登入帳戶。
1. 新增專案至購物車。
1. 使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;下訂單。
1. 在客戶儀表板中，按一下「**[!UICONTROL Purchase Orders]**」標籤。
1. 從新採購單建立訂單。 然後選取信用卡作為付款方式。
1. 同意條款與條件。
1. 下訂單。

<u>預期結果</u>：

當需要結帳的條款與條件時，您可以使用線上付款方式，對已核准的採購單下訂單。

<u>實際結果</u>：

當需要結帳的條款與條件時，您無法在已核准的採購單上使用線上付款方式下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
