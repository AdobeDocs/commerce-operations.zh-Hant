---
title: MDVA-39384：無法儲存公司使用者的自訂客戶屬性
description: MDVA-39384修補程式解決未儲存公司使用者的自訂客戶屬性的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39384。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%
---
# MDVA-39384：無法儲存公司使用者的自訂客戶屬性

MDVA-39384修補程式解決未儲存公司使用者的自訂客戶屬性的問題。 安裝[品質修補工具(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39384。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.3.6、2.4.1 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未儲存公司使用者的自訂客戶屬性。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** >設定> **組態** > **B2B功能**，並將&#x200B;**啟用公司**&#x200B;設定為「是」。
1. 建立自訂客戶屬性：
   * 必要值：是（選擇性，啟用後會顯示驗證錯誤）。
   * 在店面顯示：是。
   * Forms使用範圍：清單中的所有可用專案。
1. 建立公司並以公司管理員身分登入。
1. 導覽至您帳戶中的公司結構。
1. 按一下&#x200B;**新增使用者**&#x200B;連結。
1. 填寫包含自訂屬性的表單。
1. 按一下&#x200B;**儲存**。

<u>預期結果</u>：

自訂屬性值會與新的公司使用者一起儲存。

<u>實際結果</u>：

自訂屬性值不會與新的公司使用者一起儲存。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
