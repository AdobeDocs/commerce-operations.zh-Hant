---
title: 建立、編輯或解鎖管理員帳戶
description: 按照以下步驟管理您的Adobe Commerce或Magento Open Source管理應用程式的管理員帳戶。
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 建立、編輯或解鎖管理員帳戶

在使用此命令之前，必須執行以下操作：

- [建立部署配置](deployment.md)
- [至少啟用Magento授權和Magento用戶模組](manage-modules.md)
- 建立資料庫架構

>[!NOTE]
>
>建立資料庫的最簡單方法是使用命令 `magento setup:upgrade`。

## 建立或編輯管理員

使用此命令可建立管理員或編輯現有管理員。

>[!NOTE]
>
>如果您正在編輯管理員，則僅 `first name`。 `last name`, `password` 可以編輯。

命令用法：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

其中，下表定義了參數和值：

| 名稱 | 值 | 需要？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員用戶的名。 | 是 |
| `--admin-lastname` | 管理員用戶的姓。 | 是 |
| `--admin-email` | 管理員用戶的電子郵件地址。 | 是 |
| `--admin-user` | 管理員用戶名。 | 是 |
| `--admin-password` | 管理員用戶密碼。 密碼的長度必須至少為7個字元，並且必須至少包含一個字母和至少一個數字字元。 <br><br>我們建議使用更長、更複雜的密碼。 如果密碼字串包含需要文字解釋的特殊字元（如反斜槓或空格），請將密碼用單引號括起來。 | 是 |
| `--magento-init-params` | 添加到任何命令以自定義應用程式初始化參數<br/><br/>例如： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 否 |

用法示例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

如果未指定任何必需的參數，則應用程式會在CLI中詢問這些參數：

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

以下示例更新 `first name`。 `last name`, `password` 共 `j.doe` 管理員用戶：

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## 解鎖管理員帳戶

使用此命令可解鎖已鎖定的管理員的帳戶，這通常是由於多次登錄嘗試不正確所致。

```bash
bin/magento admin:user:unlock {username}
```

必須指定管理員的用戶名。 示例：

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

如果帳戶未解鎖或出現問題，將顯示以下消息：

```terminal
The user account "admin" was not locked or could not be unlocked
```

驗證用戶是管理員、用戶是否處於活動狀態以及帳戶是否已鎖定。 要查看管理員中鎖定用戶的清單，請以管理員身份登錄，然後按一下 **系統** > **權限** > **鎖定的用戶**。

如果帳戶不存在，將顯示以下消息：

```terminal
Couldn't find the user account "bob"
```
