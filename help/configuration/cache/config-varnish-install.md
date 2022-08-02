---
title: 安裝清漆
description: 請參閱安裝清漆的建議。
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# 安裝清漆

安裝清漆軟體超出本指南的範圍。 有關安裝清漆的詳細資訊，請參閱：

- [安裝維基](http://wiki.mikejung.biz/Varnish)
- [清漆安裝指南](https://www.varnish-cache.org/docs)
- [如何安裝清漆(Tecmint)](http://www.tecmint.com/install-varnish-cache-web-accelerator)

>[!INFO]
>
>本主題是為Muhist on CentOS和Apache 2.4編寫的。如果在不同的環境中設定清漆，則某些命令可能會有所不同。 有關詳細資訊，請參閱上面的文檔。
>
>如果要安裝清漆模組(vmod)，例如saint模式，則應通過編譯代碼來安裝清漆，而不是從包中安裝。 請參閱 [聖模式](config-varnish-advanced.md#saint-mode) 的子菜單。

## 確認清漆版本

開啟終端並輸入以下命令以顯示清漆的版本：

```bash
varnishd -V
```

示例如下：

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

確保版本為6.x，然後再繼續。 如果運行的版本低於6.x，則必須升級到受支援的版本。 有關詳細資訊，請參閱清漆安裝文檔。
