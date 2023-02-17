---
title: Security.txt
description: 了解如何提供資訊，協助安全研究人員報告漏洞。
badge: label="Kalpesh Mehta從Corra提供" type="Informity" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# 安全TXT檔案

當研究人員發現安全漏洞時，往往缺乏正確的報告渠道。 因此，系統不會回報某些弱點。 此 `security.txt` [檔案格式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) 檔案是為安全研究人員提供他們可以用來報告調查結果的資訊。

商戶可以輸入其聯繫資訊 [安全問題報告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) 從商務 _管理_. 對於開發人員， `Magento_Securitytxt` 模組提供下列功能：

- 允許從 _管理_.
- 包含路由器，用於匹配對 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 檔案。
- 提供 `.well-known/security.txt` 和 `.well-known/security.txt.sig` 檔案。

有效 `security.txt` 檔案看起來可能如下所示：

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

若要建立 `security.txt` 簽名(`security.txt.sig`)檔案：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

驗證簽名：

```bash
gpg --verify security.txt.sig security.txt
```
