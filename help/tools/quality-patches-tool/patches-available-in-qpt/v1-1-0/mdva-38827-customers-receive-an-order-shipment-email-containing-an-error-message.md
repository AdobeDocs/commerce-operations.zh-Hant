---
title: MDVA-38827：客戶透過電子郵件收到訂單出貨錯誤
description: MDVA-38827修補程式修正客戶收到包含以下錯誤訊息的訂單運送電子郵件的問題： *很抱歉，產生此內容時發生錯誤*。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-38827。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827：客戶透過電子郵件收到訂單出貨錯誤

MDVA-38827修補程式修正客戶收到訂單運送電子郵件的問題，該電子郵件包含下列錯誤訊息： *很抱歉，產生此內容時發生錯誤*。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-38827。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

選取「透過電子郵件通知客戶」出貨選項時，客戶會收到包含下列錯誤訊息的電子郵件： *很抱歉，產生此內容時發生錯誤*。

<u>要再現的步驟</u>：

1. 移至&#x200B;**行銷** > **通訊** > **電子郵件範本**，並選取&#x200B;**新增範本**。
   * 選取&#x200B;**Magento銷售** > **新出貨**。
   * 按一下&#x200B;**載入範本**。
   * 新增範本名稱（例如，核心出貨範本），然後按一下[儲存]。**&#x200B;**
1. 移至&#x200B;**商店** >設定> **設定** > **銷售** > **銷售電子郵件**：
   * 啟用&#x200B;**出貨註解**。
   * 選取[出貨註解電子郵件範本]和[客人的出貨註解電子郵件範本]下的&#x200B;**核心出貨範本** （請參閱步驟1中的[新增範本名稱]部分）。
1. 下訂單。 移至[管理]面板> **銷售** > **訂單**，按一下[**檢視**]，然後送出訂單。
1. 訂單狀態會從「擱置中」變更為「處理中」。
1. 按一下左側邊欄功能表上的&#x200B;**出貨**，然後按一下&#x200B;**檢視**&#x200B;以檢視訂單。
1. 在&#x200B;**出貨歷史記錄**&#x200B;下方的&#x200B;**註解文字**&#x200B;中新增註解，並勾選核取方塊&#x200B;**透過電子郵件通知客戶**。
1. 按一下&#x200B;**提交註解**。

<u>預期結果</u>：

已產生含出貨註解的銷售電子郵件。

<u>實際結果</u>：

電子郵件中收到下列錯誤訊息： *很抱歉，產生此內容時發生錯誤。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
