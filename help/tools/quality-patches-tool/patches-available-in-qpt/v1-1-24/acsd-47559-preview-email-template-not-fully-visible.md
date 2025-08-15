---
title: ACSD-47559：電子郵件的電子郵件範本預覽未完全顯示
description: 套用ACSD-47559修補程式，修正電子郵件範本預覽未完全可見的Adobe Commerce問題。
feature: Communications, Marketing Tools, Personalization
role: Admin
exl-id: a0bd51e0-990b-47c9-8de0-6071b6f79e54
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-47559：電子郵件範本預覽未完全可見

ACSD-47559修補程式修正電子郵件範本預覽無法完整顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html?lang=zh-Hant) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-47559。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

電子郵件範本預覽未完全可見。

<u>要再現的步驟</u>：

* 在Adobe Commerce管理員> **[!UICONTROL Marketing]** > **[!UICONTROL Communications]** > **[!UICONTROL Email Templates]**&#x200B;中新增電子郵件範本或使用現有的電子郵件範本。

<u>預期結果</u>：

預覽視窗會根據電子郵件範本大小縮放。

<u>實際結果</u>：

預覽快顯視窗會以捲動列開啟，這是預覽電子郵件範本的不便方式。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
