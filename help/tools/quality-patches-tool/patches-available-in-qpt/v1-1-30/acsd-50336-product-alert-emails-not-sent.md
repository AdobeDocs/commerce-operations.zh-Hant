---
title: ACSD-50336：產品警報電子郵件未傳送
description: 套用ACSD-50336修補程式以修正Adobe Commerce問題，即當產品重新補充庫存或價格變更時，不會傳送產品警報電子郵件。
feature: Communications, Personalization, Products
role: Admin
exl-id: 45dd12af-a3b2-4cfa-be90-af1c7b5f74b3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-50336：產品警報電子郵件未傳送

ACSD-50336修補程式修正當產品重新補充庫存或價格變更時，不會傳送產品警報電子郵件的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-50336。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當產品重新補充庫存或價格變更時，不會傳送產品警報電子郵件。

<u>必要條件</u>：

設定產品警示，以備產品新增回庫存時使用。

<u>要再現的步驟</u>：

1. 以客戶身分登入店面。
1. 開啟無庫存的產品。
1. 訂閱以在產品&#x200B;*已補充庫存*&#x200B;時收到通知。
1. 將產品從[!UICONTROL Admin]更新為&#x200B;_備貨_。

<u>預期結果</u>：

有關&#x200B;*已補貨*&#x200B;產品的電子郵件通知已傳送給客戶。

<u>實際結果</u>：

客戶未收到產品是&#x200B;*有庫存*&#x200B;的電子郵件通知。 記錄中出現下列錯誤：

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
