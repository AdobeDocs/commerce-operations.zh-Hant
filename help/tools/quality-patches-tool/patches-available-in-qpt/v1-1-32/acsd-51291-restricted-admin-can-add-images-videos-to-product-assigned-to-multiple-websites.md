---
title: ACSD-51291：受限制的管理員可將影像/影片新增至指派給多個網站的產品
description: 套用ACSD-51291修補程式以修正Adobe Commerce問題，其中存取一個網站的受限管理員可將影像/影片新增至指派給多個網站的產品。
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291：受限制的管理員可將影像/影片新增至指派給多個網站的產品

ACSD-51291修補程式修正了具有單一網站存取權的受限管理員可將影像/影片新增至指派給多個網站的產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32時，即可使用此修補程式。 修補程式ID為ACSD-51291。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p3、2.4.5 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

擁有單一網站存取權的受限管理員可將影像/影片新增至指派給多個網站的產品。

<u>要再現的步驟</u>

1. 以管理員身分登入。
1. 建立第二個網站、商店和商店檢視。
1. 使用僅供第二個網站、商店和商店檢視使用的資源，建立第二個管理員角色。
1. 建立第二個管理員，並將其指派給新的受限制管理員角色。
1. 建立新產品，並將其指派給預設網站和新網站。
1. 從主要管理員設定檔登出。
1. 以新的受限制管理員身分登入。
1. 編輯已指派給兩個網站的已建立產品。
1. 開啟&#x200B;**[!UICONTROL Images and Videos]**&#x200B;標籤。

<u>預期結果</u>：

* 系統會顯示下列訊息：

  *只有當管理員有權存取產品被指派的所有網站時，才允許受限管理員對影像或影片執行動作。*

* **[!UICONTROL Add Video]**&#x200B;按鈕未啟用。

<u>實際結果</u>：

受限管理員可以新增影像和影片，即使產品已指派給無法存取的網站。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
