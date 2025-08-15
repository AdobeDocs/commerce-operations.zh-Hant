---
title: MDVA-39163：新註冊的使用者無法從來賓工作階段取得產品的送貨方法
description: MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163：新註冊的使用者無法從來賓工作階段取得產品的送貨方法

MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

註冊新使用者時，無法使用送貨方法，且購物車中的產品來自訪客工作階段。

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理員** > **商店** > **組態** > **銷售** > **傳遞方法**。 僅啟用&#x200B;**統一費率**&#x200B;送貨方法，並停用其他所有功能。
1. 在&#x200B;**統一運費**&#x200B;送貨方式中，選取&#x200B;**送貨至適用國家/地區**&#x200B;設定中可用的&#x200B;**特定**&#x200B;國家/地區選項，並從清單中選取一個國家/地區（例如，美國）。
1. 移至&#x200B;**管理員** > **商店** > **組態** > **客戶** > **客戶組態**，並將&#x200B;**要求電子郵件確認**&#x200B;設定為&#x200B;_是_。
1. 在&#x200B;**管理員** > **行銷** > **電子郵件範本**&#x200B;中建立新的電子郵件範本，並載入`Footer (magento/luma)`範本並將範本內容取代為CMS區塊。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. 移至&#x200B;**管理員** > **內容** > **設計** > **設定**，並選取與您的前端網站相關的主題。 將「頁尾範本」設定為已建立的新電子郵件範本。
1. 前往前端，將產品新增至購物車。
1. 建立客戶；您將收到確認電子郵件地址的電子郵件。 按一下驗證連結。 您將會登入網站。
1. 移至&#x200B;**我的帳戶**&#x200B;並新增地址。 將地址國家/地區設定為您先前在管理設定中設定的送貨國家/地區。
1. 前往結帳。

<u>預期結果</u>：

送貨方式可供使用，因為客戶的地址與送貨國家/地區相容。

<u>實際結果</u>：

無法使用送貨方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
