---
title: Security.txt
description: 瞭解如何提供資訊以協助安全性研究人員報告漏洞。
feature: Configuration, Security
badge: label="由卡拉佩什·梅赫塔從科拉市撰寫" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="卡比什梅塔"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 安全性TXT檔案

當研究人員發現安全性弱點時，通常就會缺乏適當的報告管道。 因此，系統不會報告某些漏洞。 `security.txt` [檔案格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09)檔案的目的是提供安全性研究人員可用於報告其發現的資訊。

商戶可以從Commerce [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting)輸入&#x200B;_安全性問題報告_&#x200B;的連絡資訊。 對於開發人員而言，`Magento_Securitytxt`模組提供下列功能：

- 允許從&#x200B;_Admin_&#x200B;儲存安全性設定。
- 包含路由器以比對要求至`.well-known/security.txt`和`.well-known/security.txt.sig`檔案的應用程式動作類別。
- 提供`.well-known/security.txt`和`.well-known/security.txt.sig`檔案的內容。

有效的`security.txt`檔案可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

若要建立`security.txt`簽章(`security.txt.sig`)檔案：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

驗證簽章：

```bash
gpg --verify security.txt.sig security.txt
```
