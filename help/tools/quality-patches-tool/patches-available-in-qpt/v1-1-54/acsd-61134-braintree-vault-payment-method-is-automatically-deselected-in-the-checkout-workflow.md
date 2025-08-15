---
title: ACSD-61134：在結帳工作流程中自動取消選取[!UICONTROL Braintree Vault]付款方式
description: 套用ACSD-61134修補程式以解決當購物者取消選取*[!UICONTROL Braintree Vault]*核取方塊以更新其帳單地址時，在結帳工作流程中自動取消選取*[!UICONTROL My billing and shipping address are the same]*付款方法的Adobe Commerce問題。
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134：在結帳工作流程中自動取消選取&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;付款方式

ACSD-61134修補程式修正了當購物者取消選取&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;核取方塊以更新其帳單地址時，在結帳工作流程中自動取消選取&#x200B;*[!UICONTROL My billing and shipping address are the same]*&#x200B;付款方式的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61134。 請注意，此問題已排程在Adobe Commerce 2.4.7-beta1中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p7

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已在結帳工作流程中自動取消選取&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;付款方法。

<u>要再現的步驟</u>：

1. 設定&#x200B;*[!DNL Braintree]*&#x200B;付款方法，並啟用&#x200B;*[!UICONTROL Vault]*。
1. 在&#x200B;*[!UICONTROL Vault]*&#x200B;中籤出並儲存卡片。
1. 簽出另一個產品。
1. 在&#x200B;*[!UICONTROL Shipping]*&#x200B;頁面上，新增運送地址，讓您選取兩個地址。
1. 在&#x200B;*[!UICONTROL Payment]*&#x200B;頁面上，選取您的付款方式並按一下&#x200B;**[!UICONTROL My billing and shipping addresses are the same]**。

<u>預期結果</u>：

選取的付款方式仍保持選取狀態。

<u>實際結果</u>：

已取消勾選選取的付款方式。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
