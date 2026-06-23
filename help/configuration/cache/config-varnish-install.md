---
title: 安裝清漆
description: 瞭解Adobe Commerce快取的Varnish安裝需求。 探索安裝資源及設定指南。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# 安裝清漆

{{varnish-config-cloud}}

安裝Varnish超出了本指南的範圍。 本主題假設支援的Varnish版本以及在Varnish後面執行的Adobe Commerce原始伺服器。 本指南中的範例使用nginx做為原始網頁伺服器。

- [安裝指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安裝指南](https://www.varnish-cache.org/docs)
- [如何安裝清漆(Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>如果您要安裝Vmods模組(vmod) （例如saint模式），您應該編譯程式碼來安裝Varnish，而不是從套件進行安裝。 如需詳細資訊，請參閱[Saint模式](config-varnish-advanced.md#saint-mode)。

## 確認您的清漆版本

開啟終端機，然後輸入下列命令來顯示Varnish的版本：

```shell
varnishd -V
```

在繼續之前，請確定[Adobe Commerce支援](../../installation/system-requirements.md)已安裝的Varnish版本。 如果您執行的是不支援的版本，則必須升級至支援的版本。 如需詳細資訊，請參閱Varnish安裝檔案。
