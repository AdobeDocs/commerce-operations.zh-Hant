---
title: ACSD-62951：修正透過REST API傳送的[!UICONTROL Credit Memo]封電子郵件中遺漏的專案和總計
description: 套用ACSD-62951修補程式來修正Adobe Commerce的問題，也就是傳送[!UICONTROL Credit Memo]電子郵件時不含訂單專案和總計。
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951：修正透過REST API傳送的&#x200B;*[!UICONTROL Credit Memo]*&#x200B;封電子郵件中遺漏的專案和總計

ACSD-62951修補程式修正傳送[!UICONTROL Credit Memo]電子郵件時未包含訂單專案和總計的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62951。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.5-p10

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過REST API *[!UICONTROL Credit Memo]*&#x200B;建立銷退折讓單時傳送的`POST V1/order/:orderId/refund`電子郵件不包含訂單專案和總計。

<u>要再現的步驟</u>：

1. 使用任何產品建立訂單。
1. 將訂單出貨並開立商業發票。 確認已傳送發票電子郵件，並包含產品詳細資料。
1. 使用API使用者端產生管理Token。
1. 使用代號，透過REST API建立銷退折讓單。
   1. 端點： `POST V1/order/:orderId/refund`
   1. 要求裝載：

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>預期結果</u>：

*[!UICONTROL Credit Memo]*&#x200B;電子郵件應包含退款的專案與總計

<u>實際結果</u>：

*[!UICONTROL Credit Memo]*&#x200B;電子郵件不包含任何專案或總計，導致資訊不完整。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
