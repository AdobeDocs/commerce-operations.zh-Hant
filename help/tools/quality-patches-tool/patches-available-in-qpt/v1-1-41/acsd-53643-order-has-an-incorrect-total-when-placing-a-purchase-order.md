---
title: ACSD-53643：下採購單時，訂單總計不正確
description: 套用ACSD-53643修補程式，修正訂購已停用或無存貨的產品時，訂單總計有誤的Adobe Commerce問題。
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-53643：下採購單時，訂單總計不正確

ACSD-53643修補程式修正訂購停用或無庫存產品時，訂單總計有誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41時，即可使用此修補程式。 修補程式ID為ACSD-53643。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂購停用或無庫存產品的訂單時，訂單總計不正確。

<u>要再現的步驟</u>：

1. 安裝&#x200B;*[!UICONTROL B2B]*&#x200B;和&#x200B;*[!UICONTROL Inventory]*。
1. 移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]**&#x200B;並設定&#x200B;**[!UICONTROL Company]** = *是*&#x200B;和&#x200B;**[!UICONTROL Purchase Order]** = *是*。
1. 清除設定快取。
1. 建立新公司、啟用公司，以及啟用公司的&#x200B;*[!UICONTROL Purchase order]*。
1. 為公司建立新使用者。
1. 建立&#x200B;*核准規則*，由公司管理員核准所有超過&#x200B;*1 USD*&#x200B;的訂單。
1. 建立其他來源。
1. 以新公司使用者的身分登入。
1. 新增兩個產品至購物車並下訂單。
1. 停用第二個產品。
1. 以公司管理員身分登入。
1. 開啟採購單，並檢視採購單是否同時包含產品，而且總金額是兩個產品的總和。
1. 核准採購單。
1. 下訂單。
1. 開啟訂單詳細資料。

<u>預期結果</u>：

* 即使訂單中有一個產品是&#x200B;*已停用*&#x200B;或&#x200B;*無庫存*，也無法下訂單。
* *[!UICONTROL Place Order]*&#x200B;按鈕已隱藏。

<u>實際結果</u>：

已下單的訂單僅包含第一個使用中產品，但會計算兩個產品的訂單總計。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
