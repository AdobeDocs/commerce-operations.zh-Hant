---
title: ACSD-62708：管理面板中的 [!DNL TinyMCE] 7編輯器字型大小顯示PT
description: 套用ACSD-62708修補程式以修正Adobe Commerce問題，其中管理員中的 [!DNL TinyMCE] 7編輯器字型大小顯示PT而非PX。 現在，您也可以以PX來設定字型大小，而非PT。
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-62708：管理面板中的[!DNL TinyMCE] 7編輯器字型大小顯示PT

ACSD-62708修補程式解決管理面板中[!DNL TinyMCE] 7編輯器字型大小以PT而非PX顯示的問題。 此修補程式可讓您以PX設定字型大小。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62708。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理面板中的[!DNL TinyMCE] 7編輯器以PT格式顯示字型大小，而非PX格式。

<u>要再現的步驟</u>：

1. 在管理面板中開啟產品編輯頁面。
1. 展開[!UICONTROL Content]區段。
1. 檢查[!DNL TinyMCE]編輯器中的字型控制項。

<u>預期結果</u>：

字型大小應該以PX為單位。

<u>實際結果</u>：

字型大小為PT。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
