---
title: ACSD-57570：修正管理員使用者存取共用目錄的許可權受限
description: 套用ACSD-57570修補程式以修正Adobe Commerce問題，該問題導致擁有特定商店存取權的受限制管理員使用者無法一致地檢視指派給產品的所有共用目錄或儲存客戶資訊，進而導致系統不一致。
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570：修正管理員使用者存取共用目錄的許可權受限

ACSD-57570修補程式修正了具有特定存放區存取權的受限管理員使用者無法一致地檢視指派給產品的所有共用目錄或儲存客戶資訊，從而導致系統不一致的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-57570。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

有權存取特定商店的受限制管理員使用者無法一律看見所有共用目錄或儲存客戶，導致不一致。 若使用多個存放區，受限制的管理員看不到新的公司或自訂共用目錄。

<u>要再現的步驟</u>：

1. 依下列順序設定商店：
   * 建立名為W2的新網站。
   * 為預設網站建立新的商店檢視。
   * 為網站W2建立名為W2S2的新商店。
   * 為存放區W2S2建立名為W2S2SV1的新存放區檢視。
   * 為存放區W2S2建立另一個名為W2S2SV2的新存放區檢視。
   * 為W2建立公司。
1. 指派產品：
   * 僅將部分產品指派給W1。
   * 僅將部分產品指派給W2。
   * 將部分產品同時指派給W1與W2。
1. 建立自訂共用目錄，並將所有產品指派給該目錄。
1. 建立僅能存取&#x200B;**W2S2**，而非&#x200B;**W2**&#x200B;的自訂管理員角色。
1. 將受限制的管理員使用者指派給新的自訂管理員角色。
1. 以受限制的管理員使用者身分登入。
1. 驗證存取權：
   * 檢查您可以檢視的公司。
   * 檢查您可以檢視的共用目錄。
   * 開啟產品清單，並確認您是否可以看見指派產品的所有共用目錄。

<u>預期結果</u>：

行為應保持一致。

<u>實際結果</u>：

如果您只建立一個額外的網站、商店和商店檢視，則受限制的管理員使用者可以在產品清單中看到公司、共用目錄和兩個共用目錄。 透過上述設定，受限制的管理員看不到新公司或自訂共用目錄，產品清單中只會顯示「預設」共用目錄。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
