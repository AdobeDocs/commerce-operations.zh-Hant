---
title: ACSD-43887：結帳付款頁面上顯示的詳細資料不正確
description: ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887：結帳付款頁面上顯示的詳細資料不正確

ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用公司的採購單時，結帳付款頁面上會顯示不正確的詳細資料。

<u>必要條件</u>：

1. B2B模組已安裝。
1. 啟用公司設定為&#x200B;_是_。 移至&#x200B;**商店** > **設定** > **一般** > **B2B功能** > **啟用公司** > **是**。
1. 啟用採購單設定為&#x200B;_是_。 移至&#x200B;**訂單核准設定** > **啟用採購單** > **是**。
1. PayPal Express已設定為付款方式。

<u>要再現的步驟</u>：

1. 建立虛擬產品。
1. 從前端向公司管理員註冊公司帳戶。
1. 從後端核准公司帳戶，並在核准公司時將&#x200B;**啟用採購單**&#x200B;設定為&#x200B;_是_。
1. 前往前端，並使用在步驟二中建立的公司管理員帳戶登入。
1. 為公司建立「預設使用者」。 移至&#x200B;**公司使用者** > **新增使用者**。
1. 為公司建立「核准規則」。 移至&#x200B;**核准規則** > **新增規則**。

   * 規則型別：訂單總計
   * 訂單總計：大於或等於$1
   * 需要核准者：公司管理員

1. 登出並使用「預設使用者」帳戶登入。
1. 將在步驟一中建立的虛擬產品新增到購物車並繼續結帳。
1. 選取PayPal Express作為付款方式，然後按一下&#x200B;**下採購單**。
1. 登出並使用公司管理員帳戶登入。
1. 移至&#x200B;**我的採購單**，並從&#x200B;**公司採購單**，針對在步驟9中建立的訂單，按一下&#x200B;**檢視**。
1. 核准採購單。 採購單狀態應為「已核准：暫緩付款」。
1. 登出並使用公司「預設使用者」帳戶登入。
1. 移至&#x200B;**我的採購單** > **檢視** > **下訂單**。
1. 檢查&#x200B;**訂單摘要**。

<u>預期結果</u>：

訂單摘要會顯示正確的非零值。

<u>實際結果</u>：

訂單摘要總計值為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
