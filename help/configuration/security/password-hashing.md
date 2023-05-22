---
title: 密碼散列
description: 閱讀有關密碼散列策略和實現的資訊。
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 密碼散列

目前，Commerce基於不同的本機PHP散列算法，使用自己的密碼散列策略。 商業支援多種算法，如 `MD5`。 `SHA256`或 `Argon 2ID13`。 如果安裝了Na擴展（預設安裝在PHP 7.3中），則 `Argon 2ID13` 選擇為預設散列算法。 否則， `SHA256` 。 Commerce可以使用本機PHP `password_hash` 函式與Ar2i算法支援。

為了避免損害舊密碼，這些密碼已經過時的算法，例如 `MD5`，當前實現提供了一種無需更改原始口令即可升級哈希的方法。 通常，口令哈希具有以下格式：

```text
password_hash:salt:version<n>:version<n>
```

位置 `version<n>`...`version<n>` 表示密碼上使用的所有哈希算法版本。 同時，鹽總是與口令哈希一起儲存，這樣我們就可以恢復整個算法鏈。 一個示例如下：

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

第一部分表示密碼哈希。 第二， `8qnyO4H1OYIfGCUb` 就是鹽。 最後兩種算法是不同的哈希算法：1 `SHA256` 2 `Argon 2ID13`。 這意味著客戶的密碼最初是使用散列的 `SHA256` 之後，算法被更新為 `Argon 2ID13` 用氬氣重排了大麻。

## 升級哈希策略

請考慮哈希升級機制的外觀。 假設最初，密碼是使用散列 `MD5` 然後用Ar2ID13對算法進行多次更新。 下圖顯示了哈希升級流。

![哈希升級工作流](../../assets/configuration/hash-upgrade-algorithm.png)

每個散列算法都使用先前的口令散列來生成新的散列。 Commerce不儲存原始原始密碼。

![哈希升級策略](../../assets/configuration/hash-upgrade-strategy.png)

如上所述，密碼哈希可能具有應用於原始密碼的多個哈希版本。
以下是客戶驗證過程中密碼驗證機制的工作方式。

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

由於Commerce將所有使用的密碼哈希版本與密碼哈希一起儲存，所以在密碼驗證過程中可以恢復整個哈希鏈。 哈希驗證機制與哈希升級策略類似：該算法基於與口令散列一起儲存的版本，從提供的口令生成散列，並返回散列口令與資料庫儲存的散列的比較結果。

## 實施

的 `\Magento\Framework\Encryption\Encryptor` 類負責密碼哈希生成和驗證。 的 [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) 命令將客戶密碼哈希升級為最新的哈希算法。
