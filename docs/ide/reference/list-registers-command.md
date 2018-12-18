---
title: Yazmaçları Listele Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce91abde91edf989b33c476b042abaf16c685df0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704908"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
Seçili değerini kaydeder ve olanak sağlayan görüntüler göstermek için kayıtları listesini değiştirin.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
 / Görüntüleme [{`register`&#124;`registerGroup`}...]

 Belirtilen değerlerini görüntüler `register` veya `registerGroup`. Öyle değilse `register` veya `registerGroup` belirtilirse, kayıtları varsayılan listesi görüntülenir. Hiçbir anahtar belirtilirse, davranışı aynıdır. Örneğin:

 `Debug.ListRegisters /Display eax`

 eşdeğerdir

 `Debug.ListRegisters eax`

 / Listesi

 YAZMAÇ grupları listede tüm görüntüler.

 / İzleme [{`register`&#124;`registerGroup`}...]

 Bir veya daha fazla ekler `register` veya `registerGroup` değerleri listesi.

 / Unwatch [{`register`&#124;`registerGroup`}...]

 Bir veya daha fazla kaldırır `register` veya `registerGroup` listeden değerleri.

## <a name="remarks"></a>Açıklamalar
 Diğer ad `r` yerine kullanılan `Debug.ListRegisters`.

## <a name="example"></a>Örnek
 Bu örnekte `Debug.ListRegisters` diğer `r` kayıt Grup değerlerini görüntülemek için `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Hata ayıklama temelleri: Yazmaçlar penceresi](../../debugger/debugging-basics-registers-window.md)
- [Nasıl yapılır: yazmaçlar penceresini kullanma](../../debugger/how-to-use-the-registers-window.md)