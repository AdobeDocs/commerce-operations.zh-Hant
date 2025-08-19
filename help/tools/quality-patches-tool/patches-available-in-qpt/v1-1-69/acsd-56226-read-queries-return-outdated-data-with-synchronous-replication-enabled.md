---
title: ACSD-56226：READ查詢會在啟用'synchronous_replication'的情況下傳回過時的資料
description: 套用ACSD-56226修補程式以修正Adobe Commerce問題，亦即當雲端上的從屬連線啟用「synchronous_replication」旗標時，讀取查詢會傳回過時的資料。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226：讀取查詢傳回啟用`synchronous_replication`的過期資料

ACSD-56226修補程式修正了當雲端上的從屬連線啟用`synchronous_replication`旗標時，READ查詢會傳回過期資料的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-56226。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用`synchronous_replication`旗標時，讀取查詢會傳回過時的資料。 這會導致從屬連線停用，導致資料庫超載。

<u>要再現的步驟</u>：

1. 在雲端基礎結構上Adobe Commerce的環境變數中，將`MYSQL_USE_SLAVE_CONNECTION`設為&#x200B;*true*。
1. 將下列設定新增至`.magento.env.yaml`以將`synchronous_replication`設為&#x200B;*false*：

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. 重新部署並執行前端動作，例如登入、加入購物車或下訂單。

<u>預期結果</u>：

當`synchronous_replication`設定為&#x200B;*false*&#x200B;時，從屬連線仍保持啟用狀態。

<u>實際結果</u>：

當`synchronous_replication`設定為&#x200B;*false*&#x200B;時，從屬連線已停用，導致資料庫超載。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
