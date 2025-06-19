---
title: MDVA-42645：管理員無法退還已停用商店點數的獎勵積分
description: MDVA-42645修補程式解決了當商店信用功能停用時，管理員無法退款獎勵點數的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42645。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645：管理員無法退還已停用商店點數的獎勵積分

MDVA-42645修補程式解決了當商店信用功能停用時，管理員無法退款獎勵點數的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42645。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果停用商店信用功能，管理員無法退款獎勵積分。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 建立新的客戶帳戶並新增一些獎勵積分。
1. 移至&#x200B;**商店** >設定> **設定** > **客戶** > **客戶設定** > **商店點數選項**，以停用商店點數功能。
1. 以獲指派獎勵分數的客戶身分登入。
1. 新增產品至購物車並導覽至結帳。
1. 使用付款區段中的獎勵點數並下訂單。
1. 在管理員中開啟訂單，並開立商業發票。
1. 按一下&#x200B;**銷退折讓單**&#x200B;連結，以建立新的銷退折讓單。
1. 勾選底部的「退款獎勵積分」選項，然後按一下「離線退款&#x200B;**」**。

<u>預期結果</u>：

* 已成功建立銷退折讓單。
* 獎勵積分已成功退款。

<u>實際結果</u>：

您收到下列錯誤訊息： *您不能使用超過訂單金額的商店點數。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
