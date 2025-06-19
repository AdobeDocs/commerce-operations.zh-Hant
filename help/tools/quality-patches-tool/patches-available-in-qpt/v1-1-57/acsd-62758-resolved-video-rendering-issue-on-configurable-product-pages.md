---
title: ACSD-62758：解決可設定產品頁面上的視訊轉譯問題
description: 套用ACSD-62758修補程式以修正Adobe Commerce問題，亦即當URL包含預先選取的色票選項時，可設定產品詳細資料頁面上的產品影片無法正確轉譯。
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758：解決可設定產品頁面上的視訊轉譯問題

ACSD-62758修補程式修正當URL包含預先選取的色票選項時，可設定產品詳細資料頁面上的產品影片無法正確轉譯的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62758。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當URL包含預先選取的色票選項時，產品影片無法在可設定的產品詳細資料頁面上正確轉譯，導致顯示靜態影像而非影片。

<u>要再現的步驟</u>：

1. 導覽至[!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product]。
1. 選取&#x200B;**[!UICONTROL Color]**&#x200B;屬性並加以編輯。
1. 更新下列設定：
   1. 將[!UICONTROL Catalog Input Type for Store Owner]設為[!UICONTROL Visual Swatch]。
   1. 將&#x200B;**[!UICONTROL Update Product Preview Image]**&#x200B;設為&#x200B;**[!UICONTROL Yes]**。
1. 為此屬性建立一些選項。
1. 使用&#x200B;**[!UICONTROL Color]**&#x200B;屬性建立新類別並將可設定的新產品加入其中。
1. 將單一隨機影像新增至父產品。
1. 編輯新建立的可設定子產品，並將視訊新增至其媒體集：
   1. 按一下&#x200B;**[!UICONTROL Add Video]**&#x200B;並使用測試視訊URL： https://vimeo.com/12860646。
1. 儲存產品、清除快取，然後重新索引存放區。
1. 在店面中開啟新建立的產品，選取其中一個色票選項，並確認影片載入正確且顯示播放器按鈕。
1. 影片應如預期載入，且播放器按鈕應會出現。
1. 現在，以滑鼠右鍵按一下其中一個色票選項、選取&#x200B;**[!UICONTROL Inspect]**，然後找出屬性ID和選項ID。 複製產品URL並將下列專案附加至其結尾： `www.product-url.com/producit-test#attribute_id=option_id`。 這會預先選取色票選項。 在新視窗中開啟更新的URL。

<u>預期結果</u>：

視訊應正確載入，類似於手動選取色票選項時。

<u>實際結果</u>：

系統會顯示靜態影像，而非視訊。 主控台錯誤會記錄下來，表示視訊初始化失敗。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。

