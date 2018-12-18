---
title: Başlat Komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbd2d64d8103afe1e303052c9b27fc2cc85cab58
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704700"
---
# <a name="start-command"></a>Başlat Komutu
Başlangıç projesi hata ayıklama başlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
 `address`

 İsteğe bağlı. Hangi program, kaynak kodunda kesme noktası benzer durduran adresi. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerli değil.

## <a name="remarks"></a>Açıklamalar
 **Başlat** komutu çalıştırıldığında, belirtilen adresine RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
 Bu örnek, hata ayıklayıcı başlatır ve oluşan özel durumlar yok sayar.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)