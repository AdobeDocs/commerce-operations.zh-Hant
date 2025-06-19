---
title: ACSD-49849：客戶電子郵件已由PayPal電子郵件取代
description: 套用ACSD-49849修補程式，修正透過GraphQL向PayPal Express下訂單時，客戶電子郵件被PayPal電子郵件取代的Adobe Commerce問題。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849：客戶電子郵件已取代為[!DNL PayPal]電子郵件

ACSD-49849修補程式修正透過GraphQL向[!DNL PayPal Express]下訂單時，客戶的電子郵件會被[!DNL PayPal's]電子郵件取代的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49849。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過GraphQL向[!DNL PayPal Express]下訂單時，客戶的電子郵件會以[!DNL PayPal's]電子郵件取代。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**。
1. 啟用並設定[!DNL PayPal Express]並設定&#x200B;**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，並建立簡單的產品。
1. 使用GraphQL完成訪客結帳。 如需詳細資訊，請參閱Adobe Commerce開發人員檔案中的[GraphQL結帳教學課程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)。
1. 使用[!DNL PayPal Express]作為付款方式。
1. 在Adobe Commerce開發人員檔案中，記下您在[設定購物車](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/)電子郵件步驟中使用的電子郵件。
1. 下訂單後，前往Adobe Commerce管理員並檢視已建立訂單中的電子郵件。

<u>預期結果</u>：

電子郵件與結帳時設定的相同。

<u>實際結果</u>：

簽出時設定的電子郵件會被[!DNL PayPal]帳戶中設定的電子郵件覆寫。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
