---
title: Security.txt
description: 瞭解如何提供資訊以幫助安全研究人員報告漏洞。
contributor_name: Kalpesh Mehta from Corra
contributor_link: https://partners.magento.com/portal/details/partner/id/70/
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# 安全TXT檔案

當研究人員發現安全漏洞時，往往缺乏適當的報告渠道。 因此，不報告某些漏洞。 目的 `security.txt` [檔案格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 檔案是為安全研究人員提供他們可以用來報告其調查結果的資訊。

商家可以輸入其聯繫資訊 [安全問題報告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 從商務 _管理_。 對於開發商而言， `Magento_Securitytxt` 模組提供以下功能：

- 允許從 _管理_。
- 包含路由器，用於匹配請求到的應用程式操作類 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 的子菜單。
- 服務 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 的子菜單。

有效 `security.txt` 檔案可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

建立 `security.txt` 簽名(S)`security.txt.sig`)檔案：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

要驗證簽名：

```bash
gpg --verify security.txt.sig security.txt
```
