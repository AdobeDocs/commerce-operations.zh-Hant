---
title: ACSD-60441：透過V1/customers [!DNL REST] API端點更新客戶時擲回錯誤
description: 套用ACSD-60441修補程式以修正Adobe Commerce問題，其中在使用後端產生的整合存取權杖時透過V1/customers [!DNL REST] API更新客戶會擲回錯誤。
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441：透過`V1/customers` [!DNL REST] API端點更新客戶時擲回錯誤

ACSD-60441修補程式修正了使用後端產生的整合存取權杖時，透過`V1/customers` [!DNL REST] API更新客戶會導致錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-60441。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p8

**與Adobe Commerce版本**&#x200B;相容

* Adobe Commerce （所有部署方法） 2.4.4-p9、2.4.5-p8、2.4.6-p6、2.4.7-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用從後端產生的整合存取權杖時，透過`V1/customers` [!DNL REST] API端點更新客戶會擲回錯誤。

<u>要再現的步驟</u>：

1. 從管理員建立整合。
1. 使用整合權杖傳送[!DNL POST]請求給`rest/default/V1/customers/<customer_id>`。

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>預期結果</u>：

客戶資料已更新。

<u>實際結果</u>：

您會收到下列錯誤：

    &grave;&grave;json
    &lbrace;
    &grave;&grave;message&grave;： &quot;關聯網站中已存在具有相同電子郵件地址的客戶。&quot;，
    &grave;trace&quot;： ...
    &rbrace;
    &grave;&grave;

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
