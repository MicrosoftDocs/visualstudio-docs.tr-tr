---
title: Diğer Ad Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41bddec00866f7c10140abc40c5ff12c623310d3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703411"
---
# <a name="alias-command"></a>Diğer Ad Komutu
Tam komut, tam komut ve bağımsız değişkenler için yeni bir diğer ad veya başka bir diğer ad oluşturur.

> [!TIP]
> Yazmaya `>alias` herhangi bir bağımsız değişken görüntüler olmadan diğer adlar ve tanımlarını geçerli listesi.


## <a name="syntax"></a>Sözdizimi

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
 `aliasname` İsteğe bağlı. Yeni diğer ad. İçin hiçbir değer sağlanmazsa `aliasname`, geçerli diğer adlar ve tanımları listesi görüntülenir.

 `aliasstring` İsteğe bağlı. Tam komut adı veya var olan diğer ad ve bir diğer ad olarak oluşturmak istediğiniz herhangi bir parametre. İçin hiçbir değer sağlanmazsa `aliasstring`, belirtilen diğer ad görüntüler için diğer ad ve diğer ad dizesi.

## <a name="switches"></a>Anahtarlar
 / Delete/DEL ya da /d isteğe bağlı. Otomatik Tamamlama kaldırma belirtilen diğer ad siler.

 / İsteğe bağlı sıfırlayın. Önceden tanımlanmış diğer adların listesi özgün ayarlarına sıfırlar. Diğer bir deyişle, tüm ön tanımlı diğer adlar geri yükler ve tüm kullanıcı tanımlı diğer adlar kaldırır.

## <a name="remarks"></a>Açıklamalar
 Diğer adlar komutları temsil ettiği bunlar komut satırı başında yer alması gerekir.

 Bu komut verilirken komutu hemen sonra anahtarları değil sonra diğer adlar içermelidir, aksi takdirde anahtar diğer ad dizesi bir parçası olarak dahil olacaktır.

 `/reset` Anahtar diğer adları geri önce bir onay ister. Kısa form, yoktur `/reset`.

## <a name="examples"></a>Örnekler
 Bu örnek, yeni bir ad oluşturur `upper`, tam komut Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

 Bu örnek, diğer siler `upper`.

```cmd
>Tools.alias /delete upper
```

 Bu örnekte, tüm geçerli diğer adlar ve tanımları listesini görüntüler.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)