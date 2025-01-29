---
title: ACSD-46869：可設定的產品未在簽出時使用REST API進行更新
description: ACSD-46869修補程式修正了可設定產品在結帳時未使用REST API更新的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20後，即可使用此修補程式。 修補程式ID為ACSD-46869。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-46869：可設定的產品未在簽出時使用REST API進行更新

ACSD-46869修補程式修正了可設定產品在結帳時未使用REST API更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20時，即可使用此修補程式。 修補程式ID為ACSD-46869。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL QPT] 登陸頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上檢查相容性。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳期間不會使用REST API更新可設定的產品。

<u>要再現的步驟</u>：

1. 使用顏色和大小屬性建立可設定的產品。
1. 選取&#x200B;**[!UICONTROL Options]**&#x200B;並將產品加入購物車。
1. 移至&#x200B;**[!UICONTROL Checkout]**，多次更新大小（數量除外），然後檢查要求與回應。
1. 當您更新大小時，會得到下列回應。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>預期結果</u>：

會根據變更更新值。

<u>實際結果</u>：

`option_value`未更新，因此下訂單時，其大小值為舊值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* 品質修補程式工具指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tools] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需[!DNL QPT]中其他修補程式的詳細資訊，請參閱品質修補程式工具指南中 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)的[修補程式。
