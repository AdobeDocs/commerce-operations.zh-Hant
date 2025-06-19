---
title: MDVA-43491：透過CSV匯入時，基本影像標籤未更新
description: MDVA-43491修補程式修正了透過多商店網站的CSV檔案匯入時，「base_image_label」未更新的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43491。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491：透過CSV匯入時，基本影像標籤未更新

MDVA-43491修補程式修正了透過多商店網站的CSV檔案匯入時，`base_image_label`未更新的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-43491。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用多商店網站的CSV檔案匯入時，`base_image_label`不會更新。

<u>必要條件</u>：

一或多個現有的非預設網站、商店和商店檢視。

<u>要再現的步驟</u>：

1. 建立新產品。

   * 上傳影像。
   * 將產品指派給新建立的網站。

1. 將產品匯出為CSV。
1. 複製CSV檔案的預設列，更新每個存放區檢視的`base_image_label`。
1. 匯入CSV檔案。 它會正確更新每個商店的標籤，這可以在產品編輯頁面上的&#x200B;**影像和影片**&#x200B;標籤下驗證。
1. 再次匯出CSV檔案，並以不同的值更新`base_image_label`欄。
1. 再次匯入CSV檔案。
1. 在「管理員」中開啟產品，並檢查每個商店檢視的標籤是否已更新。

<u>預期結果</u>：

替代文字（影像標籤）會根據CSV檔案以存放區特有的值更新。

<u>實際結果</u>：

替代文字（影像標籤）沒有以CSV檔案中的`base_image_label`值更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
