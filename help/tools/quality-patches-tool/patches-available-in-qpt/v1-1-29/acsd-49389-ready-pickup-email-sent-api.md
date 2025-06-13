---
title: ACSD-49389：準備好接收由API傳送的電子郵件，但還沒有準備好接收時
description: 套用ACSD-49389修補程式以修正Adobe Commerce問題，亦即訂單無法收取時，API會傳送已準備好收取的電子郵件。
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389：準備好接收由API傳送的電子郵件，但還沒有準備好接收時

ACSD-49389修補程式修正了訂單無法收取時，API會傳送準備收取電子郵件的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-49389。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[QPT登陸頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)上檢查相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當訂單未準備好取貨時，API會傳送準備取貨的電子郵件。

<u>要再現的步驟</u>：

1. 啟用&#x200B;*[!UICONTROL In-Store Delivery]*&#x200B;方法。
1. 建立已啟用取貨地點的庫存來源。
1. 使用主要網站及上述建立的來源建立新庫存。
1. 建立指派相同來源的產品。
1. 設定庫存數量= 1。
1. 從店面檢視在步驟4使用&#x200B;*[!UICONTROL In-Store Delivery]*&#x200B;方法建立的產品。
1. 建立訂單的商業發票。
1. 將產品的數量設為&#x200B;*0*，並使其無庫存。
1. 發佈下列API請求：

```
{
    "orderIds": [
        1
    ]
}
```

<u>預期結果</u>：

未傳送準備取車電子郵件。

<u>實際結果</u>：

API傳回&#x200B;*訂單未準備好取貨*，但已準備好取貨電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)中可用的修補程式。
