---
title: ACSD-56515：具有網站層級許可權的管理員無法編輯[!UICONTROL Dynamic Block]
description: 套用ACSD-56515修補程式以修正具有網站層級許可權的管理員無法新增或編輯[!UICONTROL Dynamic Block]的Adobe Commerce問題。
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-56515：具有網站層級許可權的管理員無法編輯[!UICONTROL Dynamic Block]

ACSD-56515修補程式修正具有網站層級許可權的管理員無法新增或編輯[!UICONTROL Dynamic Block]的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-56515。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有網站層級許可權的管理員無法新增或編輯[!UICONTROL Dynamic Block]。

<u>要再現的步驟</u>：

1. 建立具有商店和商店的次要網站。
1. 前往「**[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**」，並使用所有可用的資源建立受限於次要網站範圍的使用者角色。
1. 以上述建立的角色建立管理員使用者。
1. 以受限制的管理員使用者登入並建立[!UICONTROL Dynamic Block]。

<u>預期結果</u>：

具有網站限制的管理員使用者可以建立[!UICONTROL Dynamic Block]。

<u>實際結果</u>：

您收到下列錯誤： *需要更多許可權才能檢視此專案*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
