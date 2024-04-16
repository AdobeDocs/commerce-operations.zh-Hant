---
title: 安裝清漆
description: 請參閱有關安裝光澤漆的建議。
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 安裝清漆

安裝Varnish軟體不屬於本指南的範圍。 如需有關安裝Varnish的詳細資訊，請參閱：

- [安裝指南](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [清漆安裝指南](https://www.varnish-cache.org/docs)
- [如何安裝清漆(Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>本主題是針對CentOS和Apache 2.4上的Varnish所撰寫。如果您是在不同的環境中設定Varnish，有些指令可能會不同。 如需詳細資訊，請參閱前述檔案。
>
>如果您要安裝Vmods模組(vmod) （例如saint模式），您應該編譯程式碼來安裝Varnish，而不是從套件進行安裝。 另請參閱 [Saint模式](config-varnish-advanced.md#saint-mode) 以取得更多詳細資料。

## 確認您的清漆版本

開啟終端機，然後輸入下列命令來顯示Varnish的版本：

```bash
varnishd -V
```

請確定 [Adobe Commerce支援](../../installation/system-requirements.md) 已安裝的Varnish版本，然後再繼續。 如果您執行的是不支援的版本，則必須升級至支援的版本。 如需詳細資訊，請參閱Varnish安裝檔案。
