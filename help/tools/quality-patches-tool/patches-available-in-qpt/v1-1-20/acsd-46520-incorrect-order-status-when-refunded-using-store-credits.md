---
title: ACSD-46520：使用商店積分退款時訂單狀態不正確
description: 本文提供解決方案，解決使用商店積分退款時，使用者會收到錯誤訂單狀態的問題。
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
source-git-commit: ab6d0a9814fe5f9dae368a1adbf99d622cdc9d92
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-46520：使用商店積分退款時訂單狀態不正確

ACSD-46520修補程式可解決使用者使用商店積分退款時，訂單狀態不正確的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-46520。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3和2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用商店積分退款時，使用者會收到錯誤的訂單狀態。

<u>要再現的步驟</u>：

1. 在店面建立客戶帳戶並登入。
1. 從管理員將商店積分指派給客戶。 商店積分應涵蓋整個訂單。
1. 使用商店積分下訂單。
1. 為訂單開立商業發票。
1. 建立銷退折讓單以退回訂單的全部金額。
選取&#x200B;**[!UICONTROL Refund to store credit]**&#x200B;核取方塊。
1. 檢查訂單狀態。

<u>預期結果</u>：

訂單狀態為&#x200B;*已關閉*。

<u>實際結果</u>：

訂單狀態為&#x200B;*Complete*，這不是正確的狀態。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或[!DNL Magento Open Source]內部部署： [品質修補工具>使用狀況](/help/tools/quality-patches-tool/usage.md) （在品質修補工具指南中）。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
