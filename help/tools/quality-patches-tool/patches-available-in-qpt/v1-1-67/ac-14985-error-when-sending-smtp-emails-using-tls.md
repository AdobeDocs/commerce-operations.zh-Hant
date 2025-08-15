---
title: AC-14985：使用TLS傳送SMTP電子郵件時發生錯誤
description: 套用AC-14985修補程式，修正Adobe Commerce使用傳輸層安全性(TLS)傳送簡單郵件傳輸通訊協定(SMTP)電子郵件時發生錯誤的問題。
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985：使用TLS傳送SMTP電子郵件時發生錯誤

AC-14985修補程式修正使用傳輸層安全性(TLS)傳送簡單郵件傳輸通訊協定(SMTP)電子郵件時發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67時，即可使用此修補程式。 修補程式ID為AC-14985。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過啟用TLS的SMTP傳送電子郵件時發生錯誤。

<u>要再現的步驟</u>：

1. 請依照以下步驟設定SMTP設定：
* 傳輸： SMTP
* 主機： url.to.smtp.host
* 連線埠：587
* SSL： TLS

<u>預期結果</u>：

成功傳送電子郵件，沒有發生錯誤。

<u>實際結果</u>：

系統會顯示下列錯誤：

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
