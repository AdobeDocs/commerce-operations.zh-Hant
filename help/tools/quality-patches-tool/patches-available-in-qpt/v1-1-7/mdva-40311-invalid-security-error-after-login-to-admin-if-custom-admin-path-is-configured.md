---
title: MDVA-40311：如果已設定自訂管理路徑，登入Admin後會出現「無效的安全性或表單金鑰」錯誤
description: MDVA-40311修補程式修正管理員使用者收到錯誤訊息：*無效安全性或表單金鑰的問題。 如果已設定自訂管理路徑且啟用秘密金鑰，請在登入管理員後重新整理頁面*。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 修補程式ID為MDVA-40311。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311：如果已設定自訂管理路徑，登入Admin後會出現「無效的安全性或表單金鑰」錯誤

MDVA-40311修補程式修正管理員使用者收到錯誤訊息的問題： *無效的安全性或表單金鑰。 如果已設定自訂管理路徑且啟用秘密金鑰，請在登入管理員後重新整理頁面*。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 修補程式ID為MDVA-40311。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者收到錯誤訊息： *無效的安全性或表單金鑰。 如果已設定自訂管理路徑且啟用秘密金鑰，請在登入管理員後重新整理頁面*。

<u>要再現的步驟</u>：

* 使用有效的使用者名稱和密碼以管理員使用者身分登入。

<u>預期結果</u>：

使用者可登入，不會出現任何錯誤訊息。

<u>實際結果</u>：

*無效的安全性或表單金鑰。 請重新整理頁面*&#x200B;錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
