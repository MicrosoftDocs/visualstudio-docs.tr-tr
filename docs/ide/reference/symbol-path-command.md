---
title: Sembol Yolu Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a27d795e5491081dca98a395c788cf8407e43e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942776"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
Simgelerini aramak hata ayıklayıcı için dizinler listesinde ayarlar.

## <a name="syntax"></a>Sözdizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
 `pathname`

 İsteğe bağlı. Noktalı virgülle ayrılmış yollar simgelerini aramak hata ayıklayıcı için listesi.

## <a name="remarks"></a>Açıklamalar
 Öyle değilse `pathname` belirtilmemişse, komut geçerli simgesi yolları listeler.

## <a name="example"></a>Örnek
 Bu örnek iki yolu simgesi dizinleri listesine ekler.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Örnek
 Bu örnek, geçerli simgesi yolları noktalı virgülle ayrılmış listesini görüntüler.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)