---
title: ACSD-60632：每次嘗試訂購時儲存的地址
description: 套用ACSD-60632修補程式以修正Adobe Commerce問題，其中新地址會與每次嘗試下訂單一併儲存，無論是否成功建立訂單。
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632：每次嘗試訂購時儲存的地址

ACSD-60632修補程式修正了每次嘗試下訂單時儲存新地址的問題，無論是否成功建立訂單。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-60632。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

每次嘗試下單時，系統都會儲存新的地址專案，無論是否成功建立訂單。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!DNL PayPal Payflow Link]**&#x200B;付款方式：
   * 在本機電腦上，系統無法接收來自[!DNL PayPal Payflow Link]的API呼叫（若沒有真正的IP）。
1. 建立簡單的產品。
1. 建立沒有地址的註冊客戶。
1. 將產品新增至購物車。
1. 繼續結帳。
1. 填入地址。 請確定在此步驟中建立了第一個地址。
1. 在&#x200B;*[!UICONTROL Review and Payments]*&#x200B;頁面上，選取&#x200B;**[!UICONTROL Credit Card (Payflow Link)]**&#x200B;選項按鈕。
1. 按一下&#x200B;**[!UICONTROL Continue]**：
   * 簽出頁面返回&#x200B;*[!UICONTROL Review and Payments]*&#x200B;步驟，並預先填入位址和預期的錯誤訊息。
1. 再次選取&#x200B;*[!UICONTROL Credit Card (Payflow Link)]*&#x200B;選項按鈕。
1. 按一下&#x200B;**[!UICONTROL Continue]**。

<u>預期結果</u>：

第二次嘗試下單時不會建立新地址。

<u>實際結果</u>：

每次嘗試下訂單後，都會建立新地址。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
